---
description: 开发中经常会遇到的问题及解决方案
---

# Angular 常见问题

## 1、angular中在html中修改class

* **html**

```markup
<div [class.shadow-checked]="shadowcheckedClass">
<button (click)="onStepChange(1)">点击</button>
```

* **css**

```css
.shadow-checked {
    box-shadow: 9px 9px 4px #006db6;
}
```

* **ts文件**

```typescript
@Input() shadowcheckedClass: boolean = false;
onStepChange(currentStep: number): void {
    switch(currentStep)
    {
      case 1:
        this.shadowcheckedClass = true;
        break;

      case 2:
        this.shadowcheckedClass = false;
        break;

      default:
        break;
    }
  }
```

HTML中的`[class.shadow-checked]="shadowcheckedClass"`，是否使用`class`中的`shadow-checked`样式，取决于后台`shadowcheckedClass`的值（`true`或者`false`）

## 2、禁用鼠标点击事件

### 2.1 禁用父元素鼠标点击事件

`event.stopPropagation()`

* **html**

```markup
<div (click)="onDeductibleChange(2,$event)" *ngIf="deductibleMagnify" ></div>
```

* **ts文件**

```typescript
onDeductibleChange(state: number,e: any): void {
    e.stopPropagation(); //阻止任何父事件处理程序被执行
    switch(state){
      case 1:
        this.deductibleMagnify = true;
        break;

      case 2:
        this.deductibleMagnify = false;
        break;

      default:
        break;
    }
  }
```

### 2.2 利用遮罩层

## 3、`*ngIf`

动态加载控件，性能不好，尽量少用

## 4、HttpClient传输url中文乱码

```typescript
encodeURIComponent(this.body);
```

## 5、输入自动聚焦下一个input，删除自动聚焦上一个input

```markup
<input type="text"
    #newPhone3
    (keyup)='focusNextInput(3, newPhone1, newPhone2, newPhone3)'
  />
```

```typescript
focusNextInput(len: number, beforeControl?: HTMLInputElement, curControl?: HTMLInputElement, nextControl?: HTMLInputElement): void {
    if (curControl.value.length < 1) {
      beforeControl?.focus();
    }
    else if (curControl.value.length === len) {
      nextControl?.focus();
    }
  }
```

## 6、keydown、 **keypress、**keyup

* keydown：按键按下时触发 
* keypress：按键按下时触发 \(针对系统按键是无效的\)
* keyup：按键松开时触发 

keydown和keypress略有不同，目前的测试是ngKeypress针对系统按键是无效的，而keydown和keyup可以。

