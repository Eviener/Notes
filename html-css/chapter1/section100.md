# HTML 常见问题

### 1. 切换tab键，不聚焦a标签

将a标签的tabindex属性设置为-1, tab键就不会聚焦在a标签上了

```markup
<a tabindex=-1>Submit</a>
```



