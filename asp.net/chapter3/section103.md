# Xamarin 控件模板

## ContentView

### 1. 控件模板

`FooterBar.xaml`模板页面代码：

```markup
<?xml version="1.0" encoding="utf-8" ?>
<ContentView xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:local="clr-namespace:MemberPortal.Extensions"
             x:Class="******.Views.Components.FooterBar">

    <StackLayout Orientation="Vertical">
        <StackLayout.Resources>
            <Color x:Key="blueColor">#1e73be</Color>
            <Style x:Key="footLabel" TargetType="Label">
                <Setter Property="FontSize" Value="12" />
                <Setter Property="FontAttributes" Value="Bold"/>
                <Setter Property="TextColor" Value="{StaticResource blueColor}"/>
                <Setter Property="VerticalTextAlignment" Value="Center"/>
            </Style>
            <Style x:Key="separator" TargetType="Label">
                <Setter Property="TextColor" Value="{StaticResource blueColor}"/>
                <Setter Property="Margin" Value="5,0"/>
                <Setter Property="VerticalTextAlignment" Value="Center"/>
            </Style>
        </StackLayout.Resources>
        <StackLayout Orientation="Horizontal" HorizontalOptions="Center">
            <Label Text="Contact Us" Style="{StaticResource footLabel}">
                <Label.GestureRecognizers>
                    <TapGestureRecognizer Tapped="ContactUs"/>
                </Label.GestureRecognizers>
            </Label>
            <Label Text="|" Style="{StaticResource separator}" />
            <Label Text="About Us" Style="{StaticResource footLabel}" >
            </Label>
            <Label Text="|" Style="{StaticResource separator}" />
            <Label Text="Disclaimer" Style="{StaticResource footLabel}" >
            </Label>
        </StackLayout>
        <StackLayout Orientation="Horizontal" HorizontalOptions="Center">
            <Label Text="Notice of Privacy Practice" Style="{StaticResource footLabel}" >
            </Label>
            <Label Text="|" Style="{StaticResource separator}" />
            <Label Text="Privacy Policy" Style="{StaticResource footLabel}" >
            </Label>
        </StackLayout>
        <StackLayout Orientation="Horizontal" HorizontalOptions="Center" Margin="0,0,0,10">
            <Label Text="Copyright 2018-2020. Alliant Health Plans,Inc. Powered by" TextColor="#000000" FontSize="9" />
            <Image Source="{local:ImageResource Source=MemberPortal.Resources.Images.logo3.png}" Scale="2.2" Margin="18,0,0,0" />
        </StackLayout>
    </StackLayout>
</ContentView>
```

`FooterBar.xaml.cs`代码

```csharp
using System;

using Xamarin.Forms;
using Xamarin.Forms.Xaml;

namespace MemberPortal.Views.Components
{
    [XamlCompilation(XamlCompilationOptions.Compile)]
    public partial class FooterBar : ContentView
    {
        public FooterBar()
        {
            InitializeComponent();
        }

        private async void ContactUs(object sender, EventArgs e)
        {
            string url = "https://www.baidu.com";
            await Navigation.PushModalAsync(new WebPage(url));
        }
    }
}
```

应用模板：

```markup
<StackLayout Orientation="Vertical" VerticalOptions="EndAndExpand">
    <controls:FooterBar />
</StackLayout>
```

### 2.数据传递

`HeaderBar.xaml`模板页面代码：

```markup
<?xml version="1.0" encoding="UTF-8"?>
<ContentView xmlns="http://xamarin.com/schemas/2014/forms" 
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:local="clr-namespace:MemberPortal.Extensions"
             x:Class="MemberPortal.Views.Components.HeaderBar"
             x:Name="this">

    <StackLayout Orientation="Vertical" BindingContext="{x:Reference this}">
        <!--logo区域-->
        <StackLayout Orientation="Horizontal" Padding="32,15" >
            <Image Source="{local:ImageResource Source=MemberPortal.Resources.Images.logo.png}" Scale="3" HeightRequest="50" Margin="0,0,70,0"   />
            <StackLayout Orientation="Vertical">
                <Label Text="Welcome" TextColor="#919191" FontSize="16" FontAttributes="Bold" />
                <Label Text="{Binding UserName}" FontSize="17" FontAttributes="Bold" TextColor="Black" />
            </StackLayout>
        </StackLayout>
    </StackLayout>
</ContentView>
```

`HeaderBar.xaml.cs`代码：

```csharp
using Xamarin.Forms;
using Xamarin.Forms.Xaml;

namespace MemberPortal.Views.Components
{
    [XamlCompilation(XamlCompilationOptions.Compile)]
    public partial class HeaderBar : ContentView
    {
        public static readonly BindableProperty UserNameProperty = BindableProperty.Create(nameof(UserName), typeof(string), typeof(HeaderBar), string.Empty);

        public string UserName
        {
            get => (string)GetValue(UserNameProperty);
            set => SetValue(UserNameProperty, value);
        }

        public HeaderBar()
        {
            InitializeComponent();
        }
    }
}
```

应用模板：

```csharp
<controls:HeaderBar x:Name="HeaderTitle" />
```

```csharp
protected override void OnAppearing()
{
    HeaderTitle.UserName = "Test";
}
```

### 3.数据传递-订阅消息（固定值）

`HeaderBar.xaml`模板页面代码：

```markup
<?xml version="1.0" encoding="UTF-8"?>
<ContentView xmlns="http://xamarin.com/schemas/2014/forms" 
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:local="clr-namespace:MemberPortal.Extensions"
             x:Class="MemberPortal.Views.Components.HeaderBar"
             x:Name="this">

    <StackLayout Orientation="Vertical" BindingContext="{x:Reference this}">
        <!--logo区域-->
        <StackLayout Orientation="Horizontal" Padding="32,15" >
            <Image Source="{local:ImageResource Source=MemberPortal.Resources.Images.logo.png}" Scale="3" HeightRequest="50" Margin="0,0,70,0"   />
            <StackLayout Orientation="Vertical">
                <Label Text="Welcome" TextColor="#919191" FontSize="16" FontAttributes="Bold" />
                <Label x:Name="UserName" FontSize="17" FontAttributes="Bold" TextColor="Black" />
            </StackLayout>
        </StackLayout>
    </StackLayout>
</ContentView>
```

`HeaderBar.xaml.cs`代码：

```csharp
using Xamarin.Forms;
using Xamarin.Forms.Xaml;

namespace MemberPortal.Views.Components
{
    [XamlCompilation(XamlCompilationOptions.Compile)]
    public partial class HeaderBar : ContentView
    {
        public HeaderBar()
        {
            InitializeComponent();
            MessagingCenter.Subscribe<Dashboard,string>(this, "MemberUser-Send:data", (sender, userName) =>
            {
                UserName.Text = userName;
            });
        }
    }
}
```

应用模板：

```csharp
<controls:HeaderBar />
```

```csharp
protected override void OnAppearing()
{
    MessagingCenter.Send<Dashboard,string>(this, "MemberUser-Send:data", "Test");
}
```

