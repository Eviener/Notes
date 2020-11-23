# Xamarin 数据绑定

## 1、绑定路径

### 1.1 后台设置BindingContext，前端获取绑定数据

```markup
<Label Text="{Binding Path=BindingContext.ImgScaleSolo}" />
```

### 1.2 CollectionView里获取BindingContext内容

```markup
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             x:Name="page">
             
	//CollectionView 通过ItemsSource绑定数据集合
	<CollectionView x:Name="coverage">
		<CollectionView.ItemTemplate>
			<DataTemplate>
				<StackLayout Orientation="Horizontal" Padding="5,0">
					<StackLayout Orientation="Vertical" VerticalOptions="Center" Margin="10,0,0,0">
						<Label Text="{Binding Source={x:Reference this}, Path=ImgScaleSolo}" /> //访问BindingContext的内容
						<Label Text="{Binding PlanName}" Style="{StaticResource label}"/> //访问ItemsSource集合中的内容
					</StackLayout>
				</StackLayout>
			</DataTemplate>
		</CollectionView.ItemTemplate>
	</CollectionView>
</ContentPage>
```

```csharp
public double ImgScaleSolo { get; set; }

public Page()
{
    InitializeComponent();
    SizeChanged += HeaderBar_SizeChanged;
}

private void HeaderBar_SizeChanged(object sender, System.EventArgs e)
{
    if (this.Width <= 375 && this.Height <= 667)
    {
        ImgScaleSolo = 0.6;
    }
    else
    {
        ImgScaleSolo = 0.8;
    }
}

protected async override void OnAppearing()
{
    base.OnAppearing();
    BindingContext = this;
}
```

