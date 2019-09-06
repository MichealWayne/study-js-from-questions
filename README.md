# Study js from questions

![js.png](http://blog.michealwayne.cn/images/icons/js.png)

- 2019.08.02��1.1.1~1.1.2
- 2019.08.09��1.1.3~1.1.4
- 2019.08.23: 1.1.5~1.1.8
- 2019.08.30: 1.1.9~1.1.10

Ŀ¼

## 1 ECMAScript-V8
### 1.1 Memory Heap/Stack(�ڴ��/ջ)
[�鿴��ϸ���� 1.1 MemoryHeap.md>>](1.1%20MemoryHeap.md)

#### 1.1.1 ������������

- Q1.`typeof null === typeof {}`�Ľ������ԭ��
- Q2.`var str1 = 'string', str2 = String('string'), str3 = new String('string');`������`str1`��`str2`��`str3`�������ͬ�����������ͬ����ͨ������ʹ����ͬ��
- Q3.�ֱ�˵�����±ȽϵĽ����ԭ��
``` js
console.log(3.0 === 3); 
console.log(+0 === -0); 
console.log(+Infinity === -Infinity);
console.log(NaN === NaN);
```
- Q4.ʲô��Number�İ�ȫ������������������Ľ����ʲô��
``` js
var num = Math.pow(2, 60);
console.log(num);
num++;
console.log(num);
num -= Math.pow(2, 59);
console.log(num);
```

- Q5.���´������ݸ�ֵ���ж��ᱨ����˳��˵˵`undefined`��`null`������
``` js
var undefined = 'undefined';
var null = 'null';
```
- Q6.���´���ִ������Ľ����ʲô��
``` js
var x = new Boolean(false);
if (x) {
    console.log('true');
} else {
    console.log('false');
}
```

- Q7.`NaN��null��undefined��true/false��Infinity`����Щ��ͨ��ȫ������ȡֵ���������`window.NaN`��nodeJs`window.null`

- Q8.����ʹ��ģ���ַ����⣬���ͨ�����ķ�ʽ��������ַ�����ֵ���������
``` js
var longString = "This is a long String
i need to wrap across multiple lines and don't want to keep in a row
because it's unreadable.";
```

- Q9.����Symbol��Ϊʲô`Symbol()`������new�����壿`consol.log(Symbol.length, String.length, Number.length)`�������ʲô��Symbol��ת��Ϊ��ֵ��


#### 1.1.2 ��������
- Q1.�ֱ�`new Array(4)`��`[,,,]`��������Ľ����һ������

- Q2.������󳤶��Ƕ��٣����������

- Q3.`console.log(Date.length, Function.length, Array.length, Object.length)`�������ʲô��



#### 1.1.3 ����ת������ȱȽ�
- Q1.�������ᱨ����������������򵥽��е�����
``` js
var numstr1 = 6.6.toFixed(2);
var numstr2 = 6.toFixed(2);
```

### Q2.`2.55.toFixed(1) === '2.6'`���ж������ʲô

- Q3.˵������ת��������ֵת���Ľ����
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

- Q4.`parseInt()`/`parseFloat()`/`Number()`/`Math.round()`����ֵת��ʱ��Ч������˳�򣬿��ԵĻ�������ԭ��˵�����Ӧ�ó�����

- Q5.����һ��`Number.prototype.toFixed()`��`Number.prototype.toPrecision()`��Ӧ�ó���

- Q6.����˫���жϵķ���ֵ��ʲô��
``` js
console.log([] == ![]);
console.log([] == '');
console.log('123.000000000000000000000000001' == 123);
console.log(false == []);
console.log(false == 0);
console.log(false == null);
console.log(Symbol('a') == false);
```


#### 1.1.4 ��̬���Ժ�Duck typing

- Q1.���������¼ӷ�������
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

- Q2.`let a = [1];`������ڲ�ɾ��/����������������ʹ`a == 'abc'`�Լ�`a++ > 456`ͬʱ������

- Q3.��һ������obj��`var obj = { 0: 1, 1: 2, 2: 3, length: 3}`����θ���������������з�������map��reduce��filter�ȵȵȵȡ�

- Q4.�����Ž���Ϊʲô�⹹�ַ����᷵�����飬��`[...'abc']` -> `['a', 'b', 'c']`��

- Q5.ֱ���޸��������͵�`valueOf()`������`toString()`��������ʲô���������˵��

#### 1.1.5 ��ֵ�ͱ�������
- Q1.������let/const��var������ֵ������

- Q2.���´���ִ�е��������ֱ���ʲô��
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

- Q3.���¸�ֵ��������������Ϊʲô
``` js
``` js
// ����1
Object.defineProperty(window, 'test', {
	writable: true,
	value: 123
});
// ����2
let test = 456;
```

``` js
// ����1
window.test2 = 'abc';
// ����2
let test2 = 'def';
```


#### 1.1.6 ִ��������
- Q1.�����������´����ִ��˳��
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


#### 1.1.7 ���������������
- Q1.���´���ִ�е��������ֱ���ʲô��

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

- Q2.`try...catch`���������к������ԣ�����Ż��Լ��к����ã�

- Q3.��������������ǿ���������Щ�����Ż���


#### 1.1.8 �հ���IIFE
### Q1.���´���ִ�е��������ֱ���ʲô��
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

### Q2.��������⣬�������յ�������ʲô����θĽ�
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

- Q3.����IIFE����Щ���á�Ӧ�ó���

#### 1.1.9 ǳ���������

#### 1.1.10 ��������


### 1.2 call Stack(���ö�ջ)

#### 1.2.1 ���ö�ջ

#### 1.2.2 �ݹ��β�ݹ�

#### 1.2.3 �첽��ص�

#### 1.2.4 ��Ϣ����

#### 1.2.5 �¼�ѭ��

#### 1.2.6 Memoization


## 2 �﷨
### 2.1 ������


#### 2.1.1 �����������͸�ֵ������

#### 2.1.2 ��λ������

#### 2.1.3 ���Ų�������Բ���Ų�����

#### 2.1.4 �⹹��չ��

#### 2.1.5 new��in

#### 2.1.6 typeof��instance

#### 2.1.7 super


### 2.2 ���ʽ�����

#### 2.2.1 block������

#### 2.2.2 break��continue

#### 2.2.3 �����ӵ�default

#### 2.2.4 for/for...in/for...of


### 2.3 ������this��call/apply/bind

#### 2.3.1 ���庯��

#### 2.3.2 arguments

#### 2.3.3 this

#### 2.3.4 call/apply/bind


### 2.4 [[prototype]]

#### 2.4.1 __ptoto__��prototype

#### 2.4.2 ԭ����


### 2.5 ���ú���

#### 2.5.1 Array�߽׺���

#### 2.5.2 Object.seal()��Object.freeze()

#### 2.5.3 Object.create()��Object.assign()

#### 2.5.4 Object.defineProperty()��Object.defineProperties()




### 2.6 ��ͼ̳�


### 2.7 Promise


### 2.8 Error



## 3 ���÷���/����
### 3.1 ���÷���

#### 3.1.1 setTimeout()��setInterval()��requestAnimationFrame()��setImmediate()

#### 3.1.2 ajax��XMLHttpRequest

### 3.2 ���ö���

#### 3.2.1 Date

#### 3.2.2 RegExp

## 4 DOM
### 4.1 ����

### 4.2 �¼�

## 5 BOM

### 5.1 ����

## 6 Webkit

## 7 Babel

## 8 Web��ȫ

-----------

������ת������ϵ���ߣ�[michealwayne@163.com](mailto:michealwayne@163.com)
