# HTML 常见问题

### 1. 切换tab键，不聚焦a标签

设置`tabindex`属性值为-1

```markup
<a tabindex=-1>Submit</a>
```

a标签、input标签，都适用。

