# 一些问题

## 1. 变量提升

js解释器会提前在内存中预留所有变量的空间，会把所有声明放到最前面，就有一个提升的概念。es6中引入的let可以克服这个问题，let 声明的变量不能在声明前调用；

## 2. bind，call 和apply

call 和 apply都可以解决js中this指向的问题，call函数接收多个参数，而apply接收一个参数数组；

* apply 、 call 、bind 三者都是用来改变函数的this对象的指向的；
* apply 、 call 、bind 三者第一个参数都是this要指向的对象，也就是想指定的上下文；
* apply 、 call 、bind 三者都可以利用后续参数传参；
* bind 是返回对应函数，便于稍后调用；apply 、call 则是立即调用 。

## 3.原型 原型链

原型和原型链是js实现ood的关键，js可以通过原型链实现继承的行为。

```js
function B() {}
B.prototype = new A();

// 等价于
class B extends A {
    constructor() {
        super();
    }
}

const b = new B()

// 等价于

var b  = {};
b.__proto__ = B.prototype;
B.call(b);
```

## 4. this

箭头函数没有this，

new语句创建的对象不会被改变this。

### 5. Promise

ES6新增的语法，用来解决回调地狱的问题。

3个状态： pending， resolved， rejected

### 6. == 和 ===

=== 是更严格的等于，检查类型和值，而==会转变值得类型来比较；

### 7.GC

新生代使用scavenge gc 算法，新生代和老生代。
老生代使用标记清除和标记压缩。

### 8.闭包

```js
function A() {
    let a = 1;
    function B() {
        console.log(a);
    }
    return B;
}
```

### 9.基本数据类型和引用类型

基本数据类型存储在栈上，引用存储类型存储在堆上；

