# TypeScript 常见问题

## 1、substr\(\) 截取字符串

```typescript
string.substr(start, length);
```

#### 参数详情

* **start** - 开始提取字符的位置（整数，小于字符串的长度）。
* **length** - 要提取的字符数。

**注意** - 如果start为负数，则substr将其用作字符串末尾的字符索引。

```typescript
let str = "Apples are round, and apples are juicy."; 
str.substr(1,2)   //pp
str.substr(-2,2)  //y.
str.substr(22)    //apples are juicy.
```

