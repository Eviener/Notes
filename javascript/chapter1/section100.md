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

## 2、日期时间处理

### 1. new Date\(\)

```typescript
const nowDate: Date = new Date();
new Date(nowDate.getFullYear(),0,1); //今年1月1日
new Date(nowDate.getFullYear(),11,31); //今年12月31日
```

1. new Date\("month dd,yyyy hh:mm:ss"\)
2. new Date\("month dd,yyyy"\)
3.  new Date\(yyyy,MM,dd,hh,mm,ss\);
4. new Date\(yyyy,MM,dd\)
5. new Date\(ms\)

month:用英文 表示月份名称，从January到December ,缩写也行（Jan....Dec）;

MM:用整数表示月份，**从0（１月）到１１（１２月）**

dd:表示一个 月中的第几天，从1到31

yyyy:四位数表示的年份

hh:小时数，从0（午夜）到23（晚11点）

mm: 分钟数，从0到59的整数

ss:秒数，从0到59的整数

ms:毫秒数，为大于等于0的整数

```javascript
var nowDate = new Date(); //当前时间
nowDate.getYear(); //获取当前年份(2位)
nowDate.getFullYear(); //获取完整的年份(4位,1970-????)
nowDate.getMonth(); //获取当前月份(0-11,0代表1月)
nowDate.getDate(); //获取当前日(1-31)
nowDate.getDay(); //获取当前星期X(0-6,0代表星期天)
nowDate.getTime(); //获取当前时间(从1970.1.1开始的毫秒数)
nowDate.getHours(); //获取当前小时数(0-23)
nowDate.getMinutes(); //获取当前分钟数(0-59)
nowDate.getSeconds(); //获取当前秒数(0-59)
nowDate.getMilliseconds(); //获取当前毫秒数(0-999)
nowDate.toLocaleDateString(); //获取当前日期
var mytime = nowDate.toLocaleTimeString(); //获取当前时间
nowDate.toLocaleString( ); //获取日期与时间
```

