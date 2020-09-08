---
description: 开发中经常会遇到的问题及解决方案
---

# jQuery 常见问题

## 1、禁用鼠标点击事件

`event.preventDefault()`

```javascript
$('a.tooltip').live('click', function(event) {
    alert("抱歉,已停用！");
    event.preventDefault();
});
```

