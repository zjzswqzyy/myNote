---
title: 类型转换
date: 2019-02-05 18:08:40
tags: javascript语法
categories: js
---

## 类型转换

<img src="https://s2.ax1x.com/2019/03/13/Ak50XD.png" alt="Ak50XD.png" border="0" class="full-image" />
<!--more-->

### 原始值到原始值转换

1. 原始值转换为布尔值，undefined null 0 -0 NaN " " 都会被转化为 false,其他都会被转为 true 
2. 原始值转化为字符串 都相当于 原始值 + ""
3. 原始值转为数字：布尔转数字 true  -> 1 false -> 0，字符串转数字： 以数字表示的字符串可以直接会转为字符串，如果字符串头尾有空格会忽略，但是空格在中间，转换结果就是 NaN。

### 原始值到对象的转换

null undefined 转为对象直接报错
原始值通过调用String(),Number()、Boolean()构造函数，转为他们各自的包装对象。

### 对象到原始值的转换

1. 对象转为布尔 都为 true，null 是 false
2. 对象到字符串：如果对象有 toString() 方法，就调用 toString() 方法。如果该方法返回原始值，就讲这个值转化为字符串。
如果对象没有 toString() 方法或者 该方法返回的不是原始值，就会调用该对象的 valueOf() 方法。如果存在就调用这个方法，如果返回值是原始值，就转化为字符串。
否则就报错。
3. 对象到数字：对象转化为数字做了跟对象转化为字符串做了想同的事儿，不同的是后者是先调用 valueOf 方法，如果调用失败或者返回不是原始值，就调用 toString 方法。
4. 一些常用内置对象 toString 方法和 valueOf 的转换规则

toString() 
    (1) Number 返回为本表示，可接受一个参数表示输出的进制数，默认为十进制
    (2) String 直接返回原字符串值
    (3) Boolean 返回文本表示 true 或 false
    (4) Object 返回 [object 类型名],Object 类型调用该方法时返回[object Object]
    (5) Array 将数组元素转为字符串，用逗号拼接并返回
    (6) Function 直接返回函数的文本声明
    (7) Date 返回日期文本表示
valueOf()
    (1) Number 返回原始类型的数字值
    (2) String 返回原始类型的字符串值
    (3) Boolean 返回原始类型的Boolean
    (4) Object 返回对象本身
    (5) Array 方法继承于Object.prototype返回原数组
    (6) Function 方法继承于Object.prototype返回函数本身
    (7) Date 方法等同于 getTime 返回时间戳

### == 运算符如何进行类型转换

1. 如果一个值是null，另一个值是undefined，则相等
2. 如果一个是字符串，另一个值是数字，则把字符串转换成数字，进行比较
3. 如果任意值是true，则把true转换成1再进行比较；如果任意值是false，则把false转换成0再进行比较
4. 如果一个是对象，另一个是数值或字符串，把对象转换成基础类型的值再比较。对象转换成基础类型，利用它的 toString 或者 valueOf 方法。 js 核心内置类，会尝试 valueOf 先于 toString（可以理解为对象优先转换成数字）；例外的是 Date，Date 利用的是 toString 转换。非 js 核心的对象，通过自己的实现中定义的方法转换成原始值。

### + 运算符如何进行类型转化

1. 一元运算 + "2" // 2
2. 二元运算 
    (1) 两边如果有字符串，另一边一会转化为字符串进行相加
    (2) 如果没有字符串，两边都会转化为数字进行相加，对象也根据前面的方法转化为原始值数字。
    (3) 如果其中的一个操作数是对象,则将对象转换成原始值，日期对象会通过 toString() 方法进行转换，其他对象通过 valueOf（）方法进行转换，但是大多数方法都是不具备可用的 valueOf() 方法，所以还是会通过 toString() 方法执行转换。


(! + [] + [] + ![]).length // 9

1. (!0 + [] + false).length
2. (true + [] + false).length
3. ("true" + false).length
4. "truefalse".length // 9


