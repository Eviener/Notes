# TypeScript 常见问题

## 1、substr\(\) 截取字符串

```typescript
string.substr(start, length);
```

#### 参数详情

* **start** - 开始提取字符的位置\(索引\)（整数，小于字符串的长度）。
* **length** - 要提取的字符数。

**注意** - 如果start为负数，则substr将其用作字符串末尾的字符索引。

```typescript
let str = "Apples are round, and apples are juicy."; 
str.substr(1,2)   //pp
str.substr(-2,2)  //y.
str.substr(22)    //apples are juicy.
```

## 2、字符串转数字

```typescript
let num = Number('123') // 123
let num = Number('abc') // NaN

//+号操作符
let num = +'123' // 123
let num = +'abc' // NaN

//判断字符串能否转换为数组
isNaN(num)
```

## 3、去除字符串中的空格

```typescript
// js实现去除空格

//去除左侧空格
function ltrim(str:string){
    const reg = /^\s+/g;
    return str.replace(reg,'');
}

//去除右侧空格
function rtrim(str:string){
    const reg = /\s+$/g;
    return str.replace(reg,'');
}

//去除两侧的空格
function trim(str:string){
    const reg = /^\s+|\s+$/g;
    return str.replace(reg,'');
}

//去除字符串中的所有空格
function trim2(str:string){
    const reg = /\s+/g;
    return str.replace(reg,'');
}
```

## 4、货币格式转金额

```typescript
function currencyConvertToNumber(currency: string): number {
  currency = currency.replace(/\$|¥|,/g, '');
  let num = isNaN(Number(currency)) ? 0 : Number(currency);
  return num;
}
```

