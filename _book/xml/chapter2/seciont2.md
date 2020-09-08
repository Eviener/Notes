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

## 2、XML Dom 转Json

### 1. TypeScript\(angular\)

help.ts文件

```typescript
export function xmlToJson(xmlDoc) {
  let obj = {};
  
  if (xmlDoc.nodeType === 1) { //xml element
    if (xmlDoc.attributes.length > 0) {
      obj["@attributes"] = {};
      for (let j = 0; j < xmlDoc.attributes.length; j++) {
        let attribute = xmlDoc.attributes.item(j);
        obj["@attributes"][attribute.nodeName] = attribute.nodeValue;
      }
    }
  } else if (xmlDoc.nodeType === 3) { //xml text
    obj = xmlDoc.nodeValue;
  }
  
  if (xmlDoc.hasChildNodes()) {
    for (let i = 0; i < xmlDoc.childNodes.length; i++) {
      let item = xmlDoc.childNodes.item(i);
      let nodeName = item.nodeName;
      if (typeof (obj[nodeName]) === 'undefined') {
        obj[nodeName] = xmlToJson(item);
      } else {
        if (typeof (obj[nodeName].push) === 'undefined') {
          let old = obj[nodeName];
          obj[nodeName] = [];
          obj[nodeName].push(old);
        }
        obj[nodeName].push(xmlToJson(item));
      }
    }
  }
  return obj;
}
```

调用

```javascript
import { xmlToJson } from '../helpers/global-helper'
//在方法里使用
let obj = xmlToJson(xmlDoc);
```

### 2. JavaScript

```javascript
function xmlToJson(xml) {
 
 // Create the return object
 var obj = {};
 if (xml.nodeType == 1) { // element
  // do attributes
  if (xml.attributes.length > 0) {
  obj["@attributes"] = {};
   for (var j = 0; j < xml.attributes.length; j++) {
    var attribute = xml.attributes.item(j);
    obj["@attributes"][attribute.nodeName] = attribute.nodeValue;
   }
  }
 } else if (xml.nodeType == 3) { // text
  obj = xml.nodeValue;
 }
 // do children
 if (xml.hasChildNodes()) {
  for(var i = 0; i < xml.childNodes.length; i++) {
   var item = xml.childNodes.item(i);
   var nodeName = item.nodeName;
   if (typeof(obj[nodeName]) == "undefined") {
    obj[nodeName] = xmlToJson(item);
   } else {
    if (typeof(obj[nodeName].push) == "undefined") {
     var old = obj[nodeName];
     obj[nodeName] = [];
     obj[nodeName].push(old);
    }
    obj[nodeName].push(xmlToJson(item));
   }
  }
 }
 return obj;
};
```

