# CSS 属性

## animation 动画

```css
div {
	animation:mymove 5s infinite;
	-webkit-animation:mymove 5s infinite; /*Safari and Chrome*/
}

@keyframes mymove {
	from {left:0px;}
	to {left:200px;}
}

@-webkit-keyframes mymove { /*Safari and Chrome*/
	from {left:0px;}
	to {left:200px;}
}
```

## background 背景

```css
div {
	background: #d5d5d5 url('image.png') no-repeat fixed center; 
}
```

## text-transform 转换文本大小写

text-transform 控制文本的大小写

```css
div{
div {
  text-transform: none; /* 默认 */
  text-transform: capitalize; /* 转换为大写字母开头 */
  text-transform: uppercase; /* 转换为大写 */
  text-transform: lowercase; /* 转换为小写 */
  text-transform: inherit; /* 继承父元素 */
}
```



