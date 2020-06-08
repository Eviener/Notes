---
description: TypeScript 包含的数据类型如下
---

# TypeScript 基本类型

##   String 字符串类型

文本数据，使用单引号（`'`）或双引号（`"`）来表示字符串类型。反引号（`````）来定义多行文本和内嵌表达式。

```typescript
let name: string = "Bobbington";
name = 'Bobbington';
let years: number = 5;
let words: string = `您好，今年是 ${ name } 发布 ${ years + 1} 周年`;
```

 还可以使用**模板字符串。**可以~~_`跨越多行`_~~并具有_嵌入式表达式_。这些字符串由反引号/反引号（`````）字符包围，并且嵌入式表达式的形式为`${ expr }`。





## number





