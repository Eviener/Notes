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

## 2、验证

```csharp
public static void AuthenticationMe()
{
    var context = new LAContext();
    NSError AuthError;
    var localizedReason = new NSString("To access secrets");

    //因为随着时间的推移，LocalAuthentication api已经被扩展，所以在设置一些属性之前需要检查iOS版本 // because LocalAuthentication APIs have been extended over time, need to check iOS version before setting some properties
    context.LocalizedFallbackTitle = "Fallback"; // iOS 8

    if (UIDevice.CurrentDevice.CheckSystemVersion(10, 0))
    {
        context.LocalizedCancelTitle = "Cancel"; // iOS 10
    }
    if (UIDevice.CurrentDevice.CheckSystemVersion(11, 0))
    {
        context.LocalizedReason = "Authorize for access to secrets"; // iOS 11
        //BiometryType = context.BiometryType == LABiometryType.TouchId ? "TouchID" : "FaceID";
    }

    //使用canEvaluatePolicy方法测试设备是否启用了TouchID或FaceID //Use canEvaluatePolicy method to test if device is TouchID or FaceID enabled
    //使用本地身份验证策略DeviceOwnerAuthenticationWithBiometrics //Use the LocalAuthentication Policy DeviceOwnerAuthenticationWithBiometrics
    if (context.CanEvaluatePolicy(LAPolicy.DeviceOwnerAuthenticationWithBiometrics, out AuthError))
    {
        //Console.WriteLine("TouchID/FaceID available/enrolled");
        replyHandler = new LAContextReplyHandler((success, error) =>
        {
            //确保它在主线程上运行，而不是在后台 //Make sure it runs on MainThread, not in Background
            if (success)
            {
                //Console.WriteLine($"You logged in with {BiometryType}!");

                //PerformSegue("AuthenticationSegue", this);
            }
            else
            {
                //Console.WriteLine(error.LocalizedDescription);
                //这里显示撤退机制 //Show fallback mechanism here
                //unAuthenticatedLabel.Text = $"{BiometryType} Authentication Failed";
                //AuthenticateButton.Hidden = true;
            }

        });
        //使用evaluatePolicy启动身份验证操作，并将UI显示为警报视图  //Use evaluatePolicy to start authentication operation and show the UI as an Alert view
        //使用本地身份验证策略  //Use the LocalAuthentication Policy DeviceOwnerAuthenticationWithBiometrics
        context.EvaluatePolicy(LAPolicy.DeviceOwnerAuthenticationWithBiometrics, localizedReason, replyHandler);
    }
    else if (context.CanEvaluatePolicy(LAPolicy.DeviceOwnerAuthentication, out AuthError))
    {
        //Console.WriteLine("When TouchID/FaceID aren't available or enrolled, use the device PIN");
        replyHandler = new LAContextReplyHandler((success, error) =>
        {
            if (success)
            {
                //Console.WriteLine($"You logged in with {BiometryType}!");

                //PerformSegue("AuthenticationSegue", this);
            }
            else
            {
                ////Console.WriteLine(error.LocalizedDescription);
                //这里显示撤退机制  //Show fallback mechanism here
                ////unAuthenticatedLabel.Text = "Device PIN Authentication Failed";
                ////AuthenticateButton.Hidden = true;
            }

        });
        //Use evaluatePolicy to start authentication operation and show the UI as an Alert view
        //Use the LocalAuthentication Policy DeviceOwnerAuthenticationWithBiometrics
        context.EvaluatePolicy(LAPolicy.DeviceOwnerAuthentication, localizedReason, replyHandler);
    }
    else
    {
        //使用evaluatePolicy启动身份验证操作，并将UI显示为警报视图 // User hasn't configured a PIN or any biometric auth. 
        //App可以实现自己的登录，也可以选择允许开放访问 // App may implement its own login, or choose to allow open access
        ////unAuthenticatedLabel.Text = "No device auth configured";

        ////var okCancelAlertController = UIAlertController.Create("No authentication", "This device does't have authentication configured.", UIAlertControllerStyle.Alert);
        ////okCancelAlertController.AddAction(UIAlertAction.Create("Use unsecured", UIAlertActionStyle.Default, alert => PerformSegue("AuthenticationSegue", this)));
        ////okCancelAlertController.AddAction(UIAlertAction.Create("Cancel", UIAlertActionStyle.Cancel, alert => Console.WriteLine("Cancel was clicked")));
        ////PresentViewController(okCancelAlertController, true, null);
    }
}
```

