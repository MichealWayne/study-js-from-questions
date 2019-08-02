# Study js from questions

![js.png](http://blog.michealwayne.cn/images/icons/js.png)

- 2019.08.02：1.1.1~1.1.5

目录

## 1 ECMAScript-V8
### 1.1 Memory Heap/Stack(内存堆/栈)
[查看详细内容 1.1 MemoryHeap.md>>](./1.1 MemoryHeap.md))

#### 1.1.1 基本数据类型

- Q1.`typeof null === typeof {}`的结果及其原因
- Q2.`var str1 = 'string', str2 = String('string'), str3 = new String('string');`，变量`str1`、`str2`和`str3`结果是相同的吗？如果不相同可能通过处理使其相同吗？
- Q3.分别说出以下比较的结果及原因：
``` js
console.log(3.0 === 3); 
console.log(+0 === -0); 
console.log(+Infinity === -Infinity);
console.log(NaN === NaN);
```
- Q4.什么是Number的安全整数？以下运算操作的结果是什么？
``` js
var num = Math.pow(2, 60);
console.log(num);
num++;
console.log(num);
num -= Math.pow(2, 59);
console.log(num);
```

- Q5.以下代码数据赋值运行都会报错吗？顺带说说`undefined`和`null`的区别
``` js
var undefined = 'undefined';
var null = 'null';
```
- Q6.以下代码执行输出的结果是什么？
``` js
var x = new Boolean(false);
if (x) {
    console.log('true');
} else {
    console.log('false');
}
```

- Q7.`NaN、null、undefined、true/false、Infinity`中哪些能通过全局属性取值？如浏览器`window.NaN`、nodeJs`window.null`

- Q8.除了使用模板字符串外，如何通过最快的方式解决以下字符串赋值报错的问题
``` js
var longString = "This is a long String
i need to wrap across multiple lines and don't want to keep in a row
because it's unreadable.";
```

- Q9.关于Symbol，为什么`Symbol()`不能用new来定义？`consol.log(Symbol.length, String.length, Number.length)`的输出是什么？Symbol能转换为数值吗？


#### 1.1.2 引用类型
- Q1.分别`new Array(4)`和`[,,,]`定义数组的结果是一样的吗？

- Q2.数组最大长度是多少？超出会如何

- Q3.`console.log(Date.length, Function.length, Array.length, Object.length)`的输出是什么？


#### 1.1.3 类型转换与相等比较
- Q1.以下语句会报错吗？如果报错如何最简单进行调整？
``` js
var numstr1 = 6.6.toFixed(2);
var numstr2 = 6.toFixed(2);
```

### Q2.`2.55.toFixed(1) === '2.6'`的判断输出是什么

- Q3.说出以下转换数字数值转换的结果：
``` js
// parseInt
parseInt('123.456.789');
parseInt('123abc');
parseInt(123.456, 36);
parseInt(123.456, 2);
parseInt(123.456, 1);

// parseFloat
parseFloat('123.456.789');
parseFloat('123abc.456.789');

// Number
Number('123a.456');
Number('0x11');
Number('0b11');
Number('0o11');

// Math.round
Math.round('123a.456');
```

- Q4.`parseInt()`/`parseFloat()`/`Number()`/`Math.round()`做数值转换时的效率排行顺序，可以的话解释下原因并说明相关应用场景。

- Q5.介绍一下`Number.prototype.toFixed()`和`Number.prototype.toPrecision()`的应用场景

#### 1.1.4 动态语言和Duck typing

- Q1.以下双等判断的返回值是什么？
``` js
console.log([] == ![]);
console.log([] == '');
console.log('123.000000000000000000000000001' == 123);
console.log(false == []);
console.log(false == 0);
console.log(false == null);
console.log(Symbol('a') == false);
```


#### 1.1.5 赋值和变量提升

#### 1.1.6 执行上下文

#### 1.1.7 作用域和作用域链

#### 1.1.8 闭包和IIFE

#### 1.1.9 浅拷贝、深拷贝

#### 1.1.10 垃圾回收


### 1.2 call Stack(调用堆栈)

#### 1.2.1 调用堆栈

#### 1.2.2 递归和尾递归

#### 1.2.3 异步与回调

#### 1.2.4 消息队列

#### 1.2.5 事件循环

#### 1.2.6 Memoization


## 2 语法
### 2.1 操作符


#### 2.1.1 算数操作符和赋值操作符

#### 2.1.2 按位操作符

#### 2.1.3 逗号操作符和圆括号操作符

#### 2.1.4 解构和展开

#### 2.1.5 new和in

#### 2.1.6 typeof和instance

#### 2.1.7 super


### 2.2 表达式和语句

#### 2.2.1 block作用域

#### 2.2.2 break和continue

#### 2.2.3 被忽视的default

#### 2.2.4 for/for...in/for...of


### 2.3 函数、this和call/apply/bind

#### 2.3.1 定义函数

#### 2.3.2 arguments

#### 2.3.3 this

#### 2.3.4 call/apply/bind


### 2.4 [[prototype]]

#### 2.4.1 __ptoto__和prototype

#### 2.4.2 原型链


### 2.5 内置函数

#### 2.5.1 Array高阶函数

#### 2.5.2 Object.seal()和Object.freeze()

#### 2.5.3 Object.create()和Object.assign()

#### 2.5.4 Object.defineProperty()和Object.defineProperties()




### 2.6 类和继承


### 2.7 Promise


### 2.8 Error



## 3 内置方法/对象
### 3.1 内置方法

#### 3.1.1 setTimeout()、setInterval()、requestAnimationFrame()、setImmediate()

#### 3.1.2 ajax和XMLHttpRequest

### 3.2 内置对象

#### 3.2.1 Date

#### 3.2.2 RegExp

## 4 DOM
### 4.1 属性

### 4.2 事件

## 5 BOM

### 5.1 缓存

## 6 Webkit

## 7 Babel

-----------

反馈和转载请联系作者：[michealwayne@163.com](mailto:michealwayne@163.com)
