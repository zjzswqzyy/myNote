---
title: let const  区别 于 var
date: 2019-02-09 12:08:40
tags: javascript语法
categories: js
---

##  let const  区别 于 var
1. 块级作用域
2. 不存在变量提升
3. 暂时性死区
4. 不可重复声明
5. let、const声明的全局变量不会挂在顶层对象下面
<img src="https://s2.ax1x.com/2019/03/14/AAiB79.png" alt="AAiJf0.jpg" border="0" class="full-image" />
<!--more-->
暂时性死区说明：
```javascript
var tmp = 123; // 声明
if (true) {
  tmp = 'abc'; // 报错 因为本区域有tmp声明变量
  let tmp; // 绑定if这个块级的作用域 不能出现tmp变量
}
```
### 注意点

1. let可以先声明稍后再赋值,而const在 声明之后必须马上赋值，否则会报错

2. const 简单类型一旦声明就不能再更改，复杂类型(数组、对象等)指针指向的地址不能更改，内部数据可以更改。

### 使用场景

1. let使用场景：变量，用以替代var。

2. const使用场景：常量、声明匿名函数、箭头函数的时候。


