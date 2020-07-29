---
description: 构建xml文档对象。在访问和操作 XML 文档之前，它必须加载到 XML DOM 对象。
---

# XML DOM 解析

大多数浏览器都有一个内建的 XML 解析器。XML 解析器读取 XML，并把它转换为 XML DOM 对象，这样才可以使用 JavaScript 访问它。

## 1、构建 XML 文档对象

### 1. XML 字符串

```javascript
var xmlText = "xml字符串内容";
if (window.DOMParser)
{
  //创建xml文档对象
  var parser = new DOMParser();
  var xmlDoc = parser.parseFromString(xmlText, "text/xml");
}
else
{
   // Internet Explorer 兼容IE
  var xmlDoc = new ActiveXObject("Microsoft.XMLDOM");
  xmlDoc.async = false;
  xmlDoc.loadXML(xmlText); 
}
```

```javascript
let xmlText = "xml字符串内容";
//创建xml文档对象
let parser = new DOMParser();
let xmlDoc = parser.parseFromString(xmlText, "text/xml");
```

 **注意：**Internet Explorer 使用 loadXML\(\) 方法来解析 XML 字符串，而其他浏览器使用 DOMParser 对象。

### 2. XML 文档

```javascript
var xhttp;
if (window.XMLHttpRequest)
{
  // IE7+, Firefox, Chrome, Opera, Safari 浏览器执行代码
  xhttp = new XMLHttpRequest();
}
else
{
  // IE6, IE5 浏览器执行代码
  xhttp = new ActiveXObject("Microsoft.XMLHTTP");
}
xhttp.open("GET","books.xml",false);
xhttp.send();
xmlDoc = xhttp.responseXML;
```

## 

