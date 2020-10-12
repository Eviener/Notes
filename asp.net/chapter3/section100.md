# Xamarin 数据传递

## 页面传值

### 1.页面添加参数

#### 1.1 PharmacyClaims页面向PharmacyClaimsDetailPage页面传值

```csharp
private async void ViewDetail(object sender, SelectionChangedEventArgs e)
{
    if (e.CurrentSelection != null && e.CurrentSelection.Count > 0)
    {
        GetPharmacyClaimsDto item = (GetPharmacyClaimsDto)e.CurrentSelection.FirstOrDefault();
        await Navigation.PushModalAsync(new PharmacyClaimsDetailPage(item));
    }
}
```

#### 1.2 PharmacyClaimsDetailPage页面接收值

```csharp
public PharmacyClaimsDetailPage(GetPharmacyClaimsDto item)
{
    InitializeComponent();
    BindingContext = item;
}
```

### 2.页面BindingContext

#### 2.1 PharmacyClaims页面向PharmacyClaimsDetailPage页面传值

```csharp
private async void ViewDetail(object sender, SelectionChangedEventArgs e)
{
    if (e.CurrentSelection != null && e.CurrentSelection.Count > 0)
    {
        GetPharmacyClaimsDto item = (GetPharmacyClaimsDto)e.CurrentSelection.FirstOrDefault();
        await Navigation.PushModalAsync(new PharmacyClaimsDetailPage
        { 
            BindingContext =  item
        });
    }
}
```

#### 2.2 PharmacyClaimsDetailPage页面接收值

```markup
<Label Text="{Binding PharmacyName}" Style="{StaticResource labelFont}"/>
```

或

```csharp
GetPharmacyClaimsDto item = (GetPharmacyClaimsDto)BindingContext;
```

## 子页面获取父页面的数据

父页面的数据绑定在BindingContext（参阅页面BindingContext），子页面：

```csharp
protected override void OnAppearing()
{
    base.OnAppearing();

    var parent = (MasterDetailPage)Parent;
    GetPharmacyClaimsDto item = (GetPharmacyClaimsDto)parent.BindingContext;  //获取父页面的数据
    BindingContext = item;  //数据绑定到页面
}
```

