# C\# 常见问题

### 1. 常用ToString\(\)方法总结

```csharp
//int,double
int num = 25;

num.ToString("C")   //￥25.00(常用的货币格式)
num.ToString("D5")  //00025(十进制数)
num.ToString("F2")  //25.00(固定点)

num = 2500000;
num.ToString("N")   //2,500,000.00(千分位格式的数字，默认为两位小数)
num.ToString("N1")  //2,500,000.0

num = 255
num.ToString("X")  //FF(十六进制)

num = 56789
string.Format("{0:N1}",num)  //56,789.0
string.Format("{0:N2}",num)  //56,789.00
string.Format("{0:N3}",num)  //56,789.000
string.Format("{0:F1}",num)  //56789.0
string.Format("{0:F2}",num)  //56789.00
(num /100.0).ToString("#.##")  //567.89
(num / 100).ToString("#.##")   //567

DateTime dt = new DateTime(2003,5,25);
dt.ToString("yyyy年MM月dd日")  //2003年05月25日
dt.ToString("yyyy/MM/dd HH:mm:ss")  //2003/05/25 时:分:秒 
```

