# C\# 常见问题

## 1. 常用ToString\(\)方法总结

### 1. int,double 数值的格式

```csharp
//int,double
int num = 25;

num.ToString("C")   //$25.00(USA)/￥25.00(China)/£25.00(UK)(专用场合的货币格式)
num.ToString("c2")  //$25.00(常用的货币格式)
num.ToString("D5")  //00025(十进制数)
num.ToString("F2")  //25.00(固定点)

num = 2500000;
num.ToString("N")   //2,500,000.00(千分位格式的数字，默认为两位小数)
num.ToString("N1")  //2,500,000.0

num = 255
num.ToString("X")  //FF(十六进制)
num = 0.4
num.ToString("p"); //40%

num = 1234
num.ToString("000000")//001234(占位符,填充位)
num.ToString("000.000")//1234.000(小数点)
num = 12345678;
num.ToString("0,00")//12,345,678(数字分组,也用于增倍器)

(num /100.0).ToString("#.##")  //123.45
(num / 100).ToString("#.##")   //123
```

### 2. Date 日期的格式化

```csharp
DateTime dt = new DateTime(2006,11,25);
dt.ToString()    //2006-11-25 10:30:25
dt.ToString("yyyy年MM月dd日")  //2006年11月25日
dt.ToString("yyyy/MM/dd HH:mm:ss")  //2006/11/25 10:30:25
dt.ToString("D")  //2006年11月25日
dt.ToString("d")  //2006-11-25
dt.ToString("F")  //2006年11月25日 10:30:25
dt.ToString("f")  //2006年11月25日 10:30
dt.ToString("s")  //2006-11-25 10:30:25
dt.ToString("T")  //10:30:25
```

以下只能单独使用，表示特定的格式：

* d ShortDatePattern
* D LongDatePattern
* f 完整日期和时间（长日期和短时间）
* F FullDateTimePattern（长日期和长时间）
* g 常规（短日期和短时间）
* G 常规（短日期和长时间）
* m、M MonthDayPattern
* r、R RFC1123Pattern
* s 使用当地时间的 SortableDateTimePattern（基于 ISO 8601）
* t ShortTimePattern
* T LongTimePattern
* u UniversalSortableDateTimePattern 用于显示通用时间的格式
* U 使用通用时间的完整日期和时间（长日期和长时间）
* y、Y YearMonthPattern

以下可以组合使用，格式化出不同的日期显示格式：

* d 月中的某一天。一位数的日期没有前导零。
* dd 月中的某一天。一位数的日期有一个前导零。
* ddd 周中某天的缩写名称，在 AbbreviatedDayNames 中定义。
* dddd 周中某天的完整名称，在 DayNames 中定义。
* M 月份数字。一位数的月份没有前导零。
* MM 月份数字。一位数的月份有一个前导零。
* MMM 月份的缩写名称，在 AbbreviatedMonthNames 中定义。
* MMMM 月份的完整名称，在 MonthNames 中定义。
* y 不包含纪元的年份。如果不包含纪元的年份小于 10，则显示不具有前导零的年份。
* yy 不包含纪元的年份。如果不包含纪元的年份小于 10，则显示具有前导零的年份。
* yyyy 包括纪元的四位数的年份。
* gg 时期或纪元。如果要设置格式的日期不具有关联的时期或纪元字符串，则忽略该模式。
* h 12 小时制的小时。一位数的小时数没有前导零。
* hh 12 小时制的小时。一位数的小时数有前导零。
* H 24 小时制的小时。一位数的小时数没有前导零。
* HH 24 小时制的小时。一位数的小时数有前导零。
* m 分钟。一位数的分钟数没有前导零。
* mm 分钟。一位数的分钟数有一个前导零。
* s 秒。一位数的秒数没有前导零。
* ss 秒。一位数的秒数有一个前导零。
* f 秒的小数精度为一位。其余数字被截断。
* ff 秒的小数精度为两位。其余数字被截断。
* fff 秒的小数精度为三位。其余数字被截断。
* ffff 秒的小数精度为四位。其余数字被截断。
* fffff 秒的小数精度为五位。其余数字被截断。
* ffffff 秒的小数精度为六位。其余数字被截断。
* fffffff 秒的小数精度为七位。其余数字被截断。
* t 在 AMDesignator 或 PMDesignator 中定义的 AM/PM 指示项的第一个字符（如果存在）。
* tt 在 AMDesignator 或 PMDesignator 中定义的 AM/PM 指示项（如果存在）。
* z 时区偏移量（“+”或“-”后面仅跟小时）。一位数的小时数没有前导零。例如，太平洋标准时间是“-8”。
* zz 时区偏移量（“+”或“-”后面仅跟小时）。一位数的小时数有前导零。例如，太平洋标准时间是“-08”。
* zzz 完整时区偏移量（“+”或“-”后面跟有小时和分钟）。一位数的小时数和分钟数有前导零。例如，太平洋标准时间是“-08:00”。
* : 在 TimeSeparator 中定义的默认时间分隔符。
* / 在 DateSeparator 中定义的默认日期分隔符。
* % c 其中 c 是格式模式（如果单独使用）。如果格式模式与原义字符或其他格式模式合并，则可以省略“%”字符。
* " c 其中 c 是任意字符。照原义显示字符。若要显示反斜杠字符，请使用“""”。

###  3. String.Format中使用格式化

```csharp
//int,double数值
int num = 56789
string.Format("{0:N1}",num)  //56,789.0
string.Format("{0:N2}",num)  //56,789.00
string.Format("{0:N3}",num)  //56,789.000
string.Format("{0:F1}",num)  //56789.0
string.Format("{0:F2}",num)  //56789.00

//Date日期
DateTime dt = DateTime.Now;
string.Format("{0:D}",dt)  //2006年11月25日
string.Format("{0:d}",dt)  //2006-11-25
string.Format("{0:F}",dt)  //2006年11月25日 10:30:25
string.Format("{0:f}",dt)  //2006年11月25日 10:30
string.Format("{0:s}",dt)  //2006-11-26 10:30:25
string.Format("{0:T}",dt)  //10:30:25
```

