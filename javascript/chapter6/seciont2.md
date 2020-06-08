---
description: TypeScript 包含的数据类型如下
---

# TypeScript 基本类型

##   string 字符串

文本数据，使用单引号（`'`）或双引号（`"`）来表示字符串类型。

还可以使用**模板字符串**，用反引号（`````）来定义多行文本和内嵌表达式`${ expr }`。可以**跨越多行**并具有**嵌入式表达式**。

```typescript
let name: string = "Bobbington";
name = 'Bobbington';
let years: number = 5;
let words: string = `您好，
    
    今年是 ${ name } 发布 ${ years + 1} 周年`;
//等效于
let words: string = "您好，\n\n"
    + "今年是 " + name + " 发布 " + (years + 1) 
    + " 周年";
```

## number 数值

双精度 64 位 **浮点值**。可以表示整数和分数。

```typescript
let decimalLiteral: number = 6; // 十进制
let hexLiteral: number = 0xf00d; //十六进制
let binaryLiteral: number = 0b1010; //二进制
let octalLiteral: number = 0o744; //八进制
```

 **注意：**`TypeScript` 和 `JavaScript` 没有整数类型。

## boolean 布尔型

表示逻辑值：`true` 和 `false`。

```typescript
let isDone: boolean = false;
```

## 数组 <a id="array"></a>

声明变量为数组。

```typescript
// 在元素类型后面加上[]
let arr: number[] = [1, 2];

// 使用数组泛型：Array<elemType>
let arr: Array<number> = [1, 2];
```

## 元组

元组类型：允许用固定数量的元素表示数组，这些元素的类型是已知的，但不必相同，对应位置的类型需要相同。

```typescript
let x: [string, number];
x = ['hello', 1];    // 运行正常
x = [1, 'hello'];    // 报错
```

当访问具有已知索引的元素时，将检索正确的类型：

```typescript
console.log(x[0].substring(1)); // OK
console.log(x[1].substring(1)); // Error, 'number' does not have 'substring'
```

访问一组已知索引之外的元素失败，并显示以下错误：

```typescript
x[3] = "world"; // Error, Property '3' does not exist on type '[string, number]'.
console.log(x[5].toString()); // Error, Property '5' does not exist on type '[string, number]'.
```

## enum 枚举

枚举类型用于定义数值集合。

 默认情况下，枚举开始于其成员编号`0`。

```typescript
enum Color {Red, Green, Blue};
let c: Color = Color.Green;
console.log(c);    // 输出 1
```

可以通过手动设置其成员之一的值来更改它。

```typescript
enum Color {Red = 1, Green, Blue}
let c: Color = Color.Green;
console.log(c);    // 输出 2
```

或者手动设置枚举中的所有值：

```typescript
enum Color {Red = 1, Green = 2, Blue = 4}
let c: Color = Color.Blue ;
console.log(c);    // 输出 4
```

 枚举的一个方便功能是，也可以在枚举中从数字值转到该值的名称。例如，根据数字值查找对应的名称：

```typescript
enum Color {Red = 1, Green, Blue}
let colorName: string = Color[2];
console.log(colorName); // Green
```

**注意：**如果某个属性的值是计算出来的，那么它后面一位的成员必须要初始化值。

```typescript
const getValue = () => {
  return 0
}

enum List {
  A = getValue(),
  B = 2,  // 此处必须要初始化值，不然编译不通过
  C
}
console.log(List.A) // 0
console.log(List.B) // 2
console.log(List.C) // 3
```

## any 任意类型

声明为 `any` 的变量可以赋予任意类型的值。是`TypeScript`针对编程时类型不明确的变量使用的一种数据类型。

我们可能需要描述编写应用程序时不知道的变量类型。这些值可能来自动态内容，例如来自用户或第三方库。在这些情况下，我们要选择退出类型检查，并让值通过编译时检查。为此，我们用`any`类型标记它们。

它常用于以下三种情况：

### 1、变量的值会动态改变时

比如来自用户的输入，任意值类型可以让这些变量**跳过**编译阶段的**类型检查**

```typescript
let x: any = 1; // 数字类型
x = 'I am who I am'; // 字符串类型
x = false; // 布尔类型
```

### 2、改写现有代码时

任意值允许在编译时可选择地包含或移除类型检查

```typescript
let x: any = 4;
x.ifItExists();    // 正确，ifItExists方法在运行时可能存在，但这里并不会检查
x.toFixed();    // 正确
```

### 3、定义存储各种类型数据的数组时

```typescript
let arrayList: any[] = [1, false, 'fine'];
arrayList[1] = 100;
```



