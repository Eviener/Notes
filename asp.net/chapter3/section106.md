# Xamarin 身份验证

## 1、IOS 检查TouchId、FaceId

```csharp
public static string CheckBiometryType()
{
    string biometryType = "None"; //生物统计学类型
    var context = new LAContext();

    if (context.CanEvaluatePolicy(LAPolicy.DeviceOwnerAuthenticationWithBiometrics, out var authError1)) //有生物识别技术(触摸或面部)
    {
        if (UIDevice.CurrentDevice.CheckSystemVersion(11, 0))
        {
            biometryType = context.BiometryType == LABiometryType.TouchId ? "TouchId" : "FaceId";
        }
        else
        {
            biometryType = "TouchId";  //iOS 11之前没有FaceID
        }
    }
    else if (context.CanEvaluatePolicy(LAPolicy.DeviceOwnerAuthentication, out var authError2))  //有设备身份验证
    {
        biometryType = "DevicePin";
    }
    else
    {
        biometryType = "None";
    }
    return biometryType;
}
```

