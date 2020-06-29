# 解析XML

### 1、构建`xml`文档对象

```javascript
var str = "xml字符串内容";
//创建xml文档对象
var parser = new DOMParser();
var xmlDoc = parser.parseFromString(str,"text/xml");
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

### 4、xml 节点

```javascript
var countrys = xmlDoc.documentElement.childNodes[0];
var country = countrys.nodeValue; //不确定正确性
```

### 5、xml获取节点数

```javascript
var countrys = xmlDoc.documentElement.childNodes;
var len = countrys.length; //返回集合中的节点数
```

