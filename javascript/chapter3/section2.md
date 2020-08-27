# Angular 路由策略

## 1、@input，@output 父子组件数据交互

父子组件数据交互

在子组件内部使用@input接受父组件传入数据，使用@output传出数据到父组件。  
[https://www.cnblogs.com/fuzitu/p/9172728.html](https://www.cnblogs.com/fuzitu/p/9172728.html)

## 2、router-outlet

参考链接：[详细介绍](https://www.cnblogs.com/sghy/p/6951083.html)、[详细介绍](https://www.jianshu.com/p/d2e0223a337d)。

## 3、重新渲染组件

参考链接：[详细介绍](https://stackoverflow.com/questions/35105374/how-to-force-a-components-re-rendering-in-angular-2)。

### 1. ChangeDetectorRef

```typescript
import { Component, OnInit, ChangeDetectorRef } from '@angular/core';

constructor(
    private cd: ChangeDetectorRef
  ) {}

ngAfterViewInit() {
    this.cd.detectChanges();
  }
```

参考链接：[详细介绍](https://www.cnblogs.com/lskzj/p/11143233.html)、[详细介绍](https://segmentfault.com/a/1190000020832397?utm_source=tag-newest)。

### 2. NgZone

### 3. ApplicationRef



## 6、ng-template、ng-content、ng-container

参考链接：[详细介绍](https://www.jianshu.com/p/0f5332f2bbf8) 和 [在线例子](https://stackblitz.com/edit/angular-component-rerender-yne23s?file=src%2Fapp%2Fapp.component.ts)。

