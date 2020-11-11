# Xamarin 设备

## 1、Device 获取设备类型

```csharp
Device.RuntimePlatform  //获取当前设备类型

//example
double top;
switch (Device.RuntimePlatform)
{
  case Device.iOS:
    top = 20;
    break;
  case Device.Android:
  case Device.UWP:
  default:
    top = 0;
    break;
}
layout.Margin = new Thickness(5, top, 5, 0);
```

## 2、DeviceInfo 设备信息

```csharp
// 设备的模型 (SMG-950U, iPhone10,6)
var device = DeviceInfo.Model;

// 设备的制造商 (Samsung)
var manufacturer = DeviceInfo.Manufacturer;

// 设备名称 (Motz's iPhone)
var deviceName = DeviceInfo.Name;

// 操作系统版本号 (7.0)
var version = DeviceInfo.VersionString;

// 平台 (Android)
var platform = DeviceInfo.Platform;

// Idiom (Phone)
var idiom = DeviceInfo.Idiom;

// 设备类型 (Physical)
var deviceType = DeviceInfo.DeviceType;
```

