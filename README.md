# Study js from questions

![js.png](http://blog.michealwayne.cn/images/icons/js.png)

- 2019.08: 1.1.x
- 2019.09: 1.2.x
- 2019.10: 2.1.x

目录

## 1 ECMAScript-V8
### 1.1 Memory Heap/Stack(内存堆/栈)
[查看详细内容 1.1 MemoryHeap.md>>](1.1%20MemoryHeap.md)

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
parseInt('abc123');
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

- Q6.以下双等判断的返回值是什么？
``` js
console.log([] == ![]);
console.log([] == '');
console.log('123.000000000000000000000000001' == 123);
console.log(false == []);
console.log(false == 0);
console.log(false == null);
console.log(Symbol('a') == false);
```


#### 1.1.4 动态语言和Duck typing

- Q1.请描述以下加法计算结果
``` js
1 + null;
1 + '2';
null + false;
false + undefined;
true + false;
[] + [];
{} + {};
{} + [];
[] + {};
{} + true;
[] + true;
'' + Symbol();
```

- Q2.`let a = [1];`，如何在不删除/增加数组项的情况下使`a == 'abc'`以及`a++ > 456`同时成立？

- Q3.有一个对象obj，`var obj = { 0: 1, 1: 2, 2: 3, length: 3}`，如何给它赋予数组的所有方法，如map、reduce、filter等等等等。

- Q4.请试着解释为什么解构字符串会返回数组，如`[...'abc']` -> `['a', 'b', 'c']`。

- Q5.直接修改引用类型的`valueOf()`方法或`toString()`方法会有什么后果？举例说明

#### 1.1.5 赋值和变量提升
- Q1.简单描述let/const与var变量赋值的区别

- Q2.以下代码执行的输出结果分别是什么？
``` js
console.log(a);
var a = 1;
```

``` js
console.log(a);
let a = 1;
```

``` js
console.log(a);
function a () { return 1 }
```

``` js
console.log(a);
var a = () => 1;
```

``` js
var a = 1;
console.log(a);
console.log(window.a);

window.a = 2;
console.log(a);
console.log(window.a)
```

``` js
let a = 1;
console.log(a);
console.log(window.a);

window.a = 2;
console.log(a);
console.log(window.a);
```

- Q3.以下赋值操作会有问题吗？为什么
``` js
``` js
// 操作1
Object.defineProperty(window, 'test', {
	writable: true,
	value: 123
});
// 操作2
let test = 456;
```

``` js
// 操作1
window.test2 = 'abc';
// 操作2
let test2 = 'def';
```


#### 1.1.6 执行上下文
- Q1.大致描述以下代码的执行顺序
``` js
function a () { console.log('a') }
function b () { console.log('b'); a(); }
function c () { console.log('c'); b(); }
c();
```

``` js
function a () { console.log('a') }
function b () { console.log('b') }
function c () { console.log('c'); new Promise((resolve) => resolve()).then(b); a(); }
c();
```


#### 1.1.7 作用域和作用域链
- Q1.以下代码执行的输出结果分别是什么？

``` js
(function (num) {
    console.log(num);
    var num = 20;
    console.log(num);
    function num() {}
    console.log(num);
})(10);
```

``` js
function a(b) {
    console.log(b);
  	var b = function () {
        console.log(b)
    }
    b();
}
a(1)
```

``` js
var name = 'World!';
(function () {
    if (typeof name === 'undefined') {
      var name = 'Jack';
      console.log('Goodbye ' + name);
    } else {
      console.log('Hello ' + name);
    }
})();
```

- Q2.`try...catch`的作用域有何特殊性？如何优化以及有何作用？

- Q3.针对作用域链我们可以做到哪些性能优化？


#### 1.1.8 闭包和IIFE
### Q1.以下代码执行的输出结果分别是什么？
``` js
var name = "gobal";
var object = {
  name : "object",
  getName: function(){
    return function(){
      return this.name;
    };
  }
};
object.getName()();
```

### Q2.经典的问题，以下最终点击会输出什么？如何改进
``` js
var items = document.querySelectorAll('li');
for(var i=0;i<items.length;i++){
    items[i].onclick = function(){
        alert(i)
    }
}
```

``` js
for (var i = 0; i < 6; i++) {
	setTimeout(function () {
		console.log(i)
	}, 1000);
}
```

- Q3.常见IIFE有哪些作用、应用场景

#### 1.1.9 浅拷贝、深拷贝
- Q1.请列举浅拷贝和深拷贝的方法

- Q2.深拷贝时遇到对象的自我调用应该如何处理？

- Q3.描述lodash的深拷贝方法_.clone/_.cloneDeep的原理逻辑

- Q4.浅拷贝和深拷贝有哪些应用场景？

#### 1.1.10 垃圾回收
- Q1.描述下“标记清除”和“引用计数”两种垃圾回收方式的原理。

- Q2.为什么要有WeakSet/WeakMap两种数据类型。它们与垃圾回收有何关系？

- Q3.WeakSet/WeakMap有哪些应用场景？


### 1.2 call Stack(调用堆栈)
[查看详细内容 1.2 CallStack.md>>](1.2%20CallStack.md)


#### 1.2.1 调用堆栈
- Q1.堆和栈的区别？js的调用堆栈指得是什么

- Q2.调用堆栈是否有限制，如果有，具体限制是什么？如何避免呢


#### 1.2.2 递归和尾递归
- Q1.什么是递归？递归会有隐患吗

- Q2.什么是尾递归？它的作用是什么？能否举个例子

#### 1.2.3 异步与回调
- Q1.js实现异步的方式和场景有哪些？

- Q2.什么是回调，你知道回调地狱么？如何解决回调地狱的问题

-  Q3.你知道Promise吗？那await/async呢？那generator函数呢？有了解过它们babel转为ES5后是啥样的么


#### 1.2.4 消息队列

- Q1.js中的消息队列是怎么样的？


- Q2.什么是宏任务？什么是微任务


#### 1.2.5 事件循环


- Q1.下面的执行代码依次输出什么？
``` html
<body>
<script>
console.log('a1');
setTimeout(function () {
	console.log('a2')
}, 0);
new Promise((resolve) => {
	console.log('a3');
	setTimeout(function () {
		console.log('a4')
	}, 0);
	resolve();
}).then(() => {
	console.log('a5')
});
console.log('a6');
</script>

<script>
console.log('b1');
setTimeout(function () {
	console.log('b2')
}, 0);
new Promise((resolve) => {
	console.log('b3');
	setTimeout(function () {
		console.log('b4')
	}, 0);
	resolve();
}).then(() => {
	console.log('b5')
});
console.log('b6');
</script>
</body>
```

- Q2.简单描述下事件循环的机制，浏览器环境与nodejs环境下的事件循环有区别吗？


#### 1.2.6 Memoization

- Q1.Memoization是什么？

- Q2.Memoization的应用场景是什么？

## 2 语法
### 2.1 操作符

[查看详细内容 2.1 Operators.md>>](2.1%20Operators.md)

#### 2.1.1 算数操作符和赋值操作符

- Q1.以下基本数据类型的加号运算的结果是什么？
```
1 + 2
1 + '2'
1 + false
'1' + false
1 + null
'1' + null
1 + undefined
'1' + undefined
false + null
Undefined + false
1 + Symbol()
1 + 1n
'1' + 1n
```

- Q2.以下涉及到引用类型的加号运算的结果是什么？
```
[] + []
{} + []
[] + {}
0 + {}
{} + 0
[] + 0
0 + {}
new Set() + new Set()
new Map() + new Map()
```

- Q3.`0.03 % 0.01`的结果是什么？求余运算需要注意什么？

- Q4.ES7新增的幂运算操作符是什么？

- Q5.连等赋值需要注意什么？


#### 2.1.2 按位操作符

- Q1.了解过标志位与掩码么？有何作用？

- Q2.用按位非`~`判断索引存在的原理是什么？如`~'123test123'.indexOf('test')`

- Q3.左移/右移操作符有哪些用？无符号左移/右移呢？

- Q4.请用按位操作符实现经典题：不能使用额外的变量或内容空间来交换两个整数的值，如`a = 1; b = 2`


#### 2.1.3 逗号操作符和圆括号操作符

- Q1.逗号操作符的运作模式是怎么样的？

- Q2.逗号操作符有哪些常见使用场景？批量变量赋值使用逗号操作符和不使用有何区别？

- Q3.圆括号操作符的运作模式和应用场景是怎么样的？

#### 2.1.4 解构和展开

- Q1.解构和展开的运作模式是怎么样的？有了解过它babel后的结果吗？

- Q2.为什么展开运算符能解构字符串？如`[...'test']`

- Q3.请用解构赋值实现经典题：不能使用额外的变量或内容空间来交换两个整数的值，如`a = 1; b = 2`

#### 2.1.5 new和in

- Q1.经典题：自己撸一个函数来实现new运算符

- Q2.in操作符的运作模式

#### 2.1.6 typeof和instanceof

- Q1.typeof的检测原理

- Q2.instanceof的检测原理

- Q3.写一个数据类型检测方法

#### 2.1.7 super

- Q1.super关键字是用来干嘛的？

- Q2.super的prop属性有什么意义？

### 2.2 表达式和语句

[查看详细内容 2.2 Expression.md>>](2.1%20Expression.md)

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

## 8 Web安全

-----------

反馈和转载请联系作者：[michealwayne@163.com](mailto:michealwayne@163.com)
