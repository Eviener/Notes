# JavaScript 常见问题

## 1、截取字符串

### 1. substring\(\)

```javascript
string.substring(indexStart, indexEnd);
```

#### 参数详情

* **indexStart** - 开始提取字符的位置\(索引\)（整数，小于字符串的长度）。
* **indexEnd** - 结束索引（整数，小于字符串的长度）。

### 2. substr\(\)

```javascript
string.substr(start, length);
```

#### 参数详情

* **start** - 开始提取字符的位置\(索引\)（整数，小于字符串的长度）。
* **length** - 要提取的字符数。

### 3. slice\(\)

```javascript
string.slice(beginIndex, endIndex);
```

#### 参数详情

* **beginIndex** - 开始提取字符的位置\(索引\)（整数，小于字符串的长度）。
* **endIndex** - 结束索引（整数，小于字符串的长度）。

#### 返回值

返回一个索引和另一个索引之间的字符串

更多详情请参阅[博客园](https://www.cnblogs.com/wangyulue/p/7718532.html)。

