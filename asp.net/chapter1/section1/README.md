# C\# 简介

```csharp
//箭头函数
int Person(int num) => num * 12;
```

```csharp
public class UnitConverter
{
    int ratio;
    public UnitConverter (int unitRatio)
    {
        ratio = unitRatio;
    }
    public int Convert (int unit)
    {
        return unit * ratio;
    }
}

class Test
{
    static void Main()
    {
        UnitConverter feet = new UnitConverter(12);
        UnitConverter miles = new UnitConverter(5280);

        Console.WriteLine(feet.Convert(30)); //360
        Console.WriteLine(feet.Convert(miles.Convert(1))); //63360
    }
}
```

