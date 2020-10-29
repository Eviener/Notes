# Xamarin 图片

## 1、图片显示

```markup
<AbsoluteLayout>
    <Image x:Name="TempIDCard" WidthRequest="717" HeightRequest="230">
        <Image.GestureRecognizers>
            <TapGestureRecognizer Tapped="PinchIdCard" NumberOfTapsRequired="1"/>
        </Image.GestureRecognizers>
    </Image>
</AbsoluteLayout>
```



