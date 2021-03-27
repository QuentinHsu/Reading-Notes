# this

## 基本规则

* 在函数体中，非显式或隐式地简单调用函数时，在严格模式下，函数内的 this 会被绑定到 undefined 上，在非严格模式下则会被绑定到全局对象 window/global 上。
* 一般使用 new 方法调用构造函数时，构造函数内的 this 会被绑定到新创建的对象上。
* 一般通过 call/apply/bind 方法显式调用函数时，函数体内的 this 会被绑定到指定参数的对象上。
* 一般通过上下文对象调用函数时，函数体内的 this 会被绑定到该对象上。
* 在箭头函数中，this 的指向是由外层（函数或全局）作用域来决定的。

## 全局环境中的 this

```javascript
function f1() {
  console.log(this)
}

function f2() {
  'use strict'
  console.log(this)
}

f1()  // this = 全局对象
f2()  // this = undefined
```

函数直接在全局环境中调用

* 在非严格模式下，this 指向全局对象。
  * 浏览器：window。
* 在严格模式下，this 指向 undefined。

```javascript
const foo = {
  bar: 10,
  fn: function (params) {
    console.log(this)
    console.log(this.bar)
  }
}
var fn1 = foo.fn
fn1()
// 全局对象
// undefined
```

在这里，this 仍指向全局对象。

因为 foo.fn 赋值给了 fn1，fn1 又接着在全局环境中执行。this 就脱离了 foo，到了全局环境中了。

```javascript
const foo = {
  bar: 10,
  fn: function (params) {
    console.log(this)
    console.log(this.bar)
  }
}
foo.fn()
// { bar: 10, fn: [Function: fn] }
// 10
```

而这里是通过 foo 去调用其内部的 fn，那么这里的 this 指向的是调用它的对象，也就是 foo。

