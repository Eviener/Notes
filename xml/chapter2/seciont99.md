# XML DOM 常用方法归纳

### 1、构建`xml`文档对象

```javascript
let xmlText = "xml字符串内容";
//创建xml文档对象
let parser = new DOMParser();
let xmlDoc = parser.parseFromString(xmlText, "text/xml");
```

### 2、xml查找节点

```javascript
//提取数据
var countrys = xmlDoc.getElementsByTagName('DataSource');
```

### 3、xml 获取节点的文本值

```javascript
var countrys = xmlDoc.getElementsByTagName('DataSource');
var country = countrys[0].textContent;
```

### 4、xml 获取节点的文本值、节点名称

```javascript
var countrys = xmlDoc.documentElement.childNodes[0];
var country = countrys.nodeValue; //节点文本值
```

### 5、xml获取节点数

```javascript
var countrys = xmlDoc.documentElement.childNodes;
var len = countrys.length; //返回集合中的节点数
```

### 6、xml Dom 转 json

```javascript
let obj = xmlToJson(xmlDoc);
```

