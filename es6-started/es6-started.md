# es6快速入门

![es6](http://7xiqdg.com1.z0.glb.clouddn.com/introduction-into-es6-javascript-5-638-560x314.jpg)

### ES6简介

ECMAScript 6.0（以下简称ES6）是JavaScript语言的下一代标准，已经在2015年6月正式发布了。它的目标，是使得JavaScript语言可以用来编写复杂的大型应用程序，成为企业级开发语言。

**ES6与ECMAScript2015的关系**

ES6的第一个版本，就这样在2015年6月发布了，正式名称就是《ECMAScript 2015标准》（简称ES2015）。，ES6既是一个历史名词，也是一个泛指，含义是5.1版以后的JavaScript的下一代标准，涵盖了ES2015、ES2016、ES2017等等，而ES2015则是正式名称，特指该年发布的正式版本的语言标准。

所以，我们可以认为ES6 = ES2015

![呵呵](http://7xiqdg.com1.z0.glb.clouddn.com/timg.jpeg)


### Babel

由于不是目前所有的浏览器都能兼容ES6的全部特性，所以实际的项目还是主要有ES5语法来开发。

这里可以看到 es6在各大浏览器的支持程度[http://kangax.github.io/compat-table/es6/](http://kangax.github.io/compat-table/es6/)

但是ES6毕竟是以后的标准，而且约来越多的项目已经在用ES6开发了，你需要看懂别的人写的代码，同时让自己写的代码让别人看懂，最重要的是如果有天妹子问你，啥是ES6呀？

![问号](http://7xiqdg.com1.z0.glb.clouddn.com/question.jpeg)

Babel是一个广泛使用的ES6转码器，可以将ES6代码转为ES5代码，从而在现有环境执行。可以去官网了解一下[https://babeljs.io/](https://babeljs.io/)

Babel做的事情很简单，将ES6语法写出的代码，解析成ES5的语法，从而使得目前所有的浏览器都能正常运行。

比如：
```
// 转码前
input.map(item => item + 1);

// 转码后
input.map(function (item) {
  return item + 1;
});
```
可以在babel官网上，在线查看ES6代码转换成ES5是什么样子的。

[http://babeljs.io/repl/](http://babeljs.io/repl/) 有时候不太稳定，可能需要翻一下 ┑(￣Д ￣)┍

在项目中使用babel需要配置.babelrc文件，存放在项目根目录下。

先安装 bable-cli
```
npm install babel-cli -g
```
然后安装一个将es6编译成es5的插件
```
npm install --save-dev babel-preset-es2015
```
将.babelrc中添加这个配置
```
{
    "presets": ["es2015"],
    "plugins": []
  }
```
然后运行
```
babel es6.js -o es5.js
```

就可以看到es5.js就是解析过后的脚本

babel有大量的插件，还需要大家自己去了解。

### 常用语法

#### let,const

##### let

let和const的用法都类似var。let是块级作用域声明，所声明的变量，只在let所在的代码块内有效。
```
{
  let a = 10;
  var b = 1;
}

a // ReferenceError: a is not defined.
b // 1
```
最为典型的例子，for循环
```
var a = [];
for (var i = 0; i < 10; i++) {
  a[i] = function () {
    console.log(i);
  };
}
a[6](); // 10
```
我们往往需要使用闭包的手法来处理
```
var a = [];
for (var i = 0; i < 10; i++) {
  (function(i){
    a[i] = function () {
    console.log(i);
    };
  })(i);
}
a[6]();  //6
```
换成let会方便很多
```
var a = [];
for (let i = 0; i < 10; i++) {
  a[i] = function () {
    console.log(i);
  };
}
a[6](); // 6
```
**变量提升问题**

var声明会存在变量提升的问题，如果变量在声明前使用，其值则会输出 undefined。let声明则改变了这种奇怪的逻辑，let所声明的变量必须先声明，后使用，否则就会报错。
```
// var 的情况
console.log(foo); // undefined
var foo = 2;

// let 的情况
console.log(bar); // ReferenceError
let bar = 2;
```
**不能重复声明**

和var不同，let不允许在相同作用域中，重复声明同一个变量。
```
// 正常
function () {
  var a = 10;
  var a = 1;
}
// 报错
function () {
  let a = 10;
  var a = 1;
}

// 报错
function () {
  let a = 10;
  let a = 1;
}
```

##### const

const用来声明一个常量。一旦声明，常量的值就不能改变。而且声明后必须立即初始化赋值，不能后面赋值。
```
//报错
const PI = 3.1415;
PI // 3.1415
PI = 3;

//报错
const DOMAIN;
DOMAIN = 'jd.com';
```

const和let很相似：1.只在块级作用域中有效，2.不会提升变量，3.不能重复定义变量。

const声明的变量虽然无法改变，但是const命令只是保证所赋值的变量指向的地址不变，并不保证改地址的数据不变，所以当赋值的变量是一个值引用型的变量的时候，要格外的小心。

#### Class

JavaScript语言的传统方法是通过构造函数，定义并生成新对象。
```
function Human(name) {
  this.name = name;
}

Human.prototype.sayName = function () {
  return '(My name is' + this.name + )';
};
var zhang3 = new Human('zhang3');
var li4 = new Human('li4');
var wang5 = new Human('wang5');
```

ES6提供了更接近传统语言(C++和Java)的写法，引入了Class（类）这个概念，作为对象的模板。通过class关键字，可以定义类。基本上，ES6的class可以看作只是一个语法糖，它的绝大部分功能，ES5都可以做到，新的class写法只是让对象原型的写法更加清晰、更像面向对象编程的语法而已。上面的代码用ES6的“类”改写，就是下面这样。

```
class Human {
  constructor(name) {
    this.name = name;
  }
  sayName() {
    return '(My name is' + this.name + )';
  }
}

var zhang3 = new Human('zhang3');
var li4 = new Human('li4');
var wang5 = new Human('wang5');
```
**constructor**

constructor方法是类的默认方法，通过new命令生成对象实例时，自动调用该方法。一个类必须有constructor方法，如果没有显式定义，一个空的constructor方法会被默认添加。

constructor方法默认返回实例对象（即this），可以指定返回另外一个对象。
```
class Foo {
  constructor() {
    return Object.create(null);
  }
}

new Foo() instanceof Foo
// false
```
**extends**

Class之间可以通过extends关键字实现继承，这比ES5的通过修改原型链实现继承，要清晰和方便很多。
```
class Woman extends Human {
  constructor(name) {
    super(name); // 调用父类的constructor(name);
    this.sex = 'female';
  }
}

let hanmeimei = new Woman('hanmeimei');
```

#### =>

需要用函数表达式的地方，可以用=>代替，代码简洁，而且绑定了this.

```
// bad
[1, 2, 3].map(function (x) {
  return x * x;
});

// good
[1, 2, 3].map((x) => {
  return x * x;
});

// best
[1, 2, 3].map(x => x * x);
```
箭头函数取代Function.prototype.bind
```
// bad
const self = this;
const boundMethod = function(...params) {
  return method.apply(self, params);
}

// acceptable
const boundMethod = method.bind(this);

// best
const boundMethod = (...params) => method.apply(this, params);
```

#### 解构

ES6 允许按照一定模式，从数组和对象中提取值，对变量进行赋值，这被称为解构（Destructuring）。

没明白啥意思，show me the code

![](http://7xiqdg.com1.z0.glb.clouddn.com/linus.jpg)

数组解构赋值
```
// before
let a = 1;
let b = 2;
let c = 3;
//after
let [a, b, c] = [1, 2, 3];
let [foo, [[bar], baz]] = [1, [[2], 3]];
let [ , , third] = ["foo", "bar", "baz"];
```
对象解构赋值
```
let { foo, bar } = { foo: "aaa", bar: "bbb" };
let { bar, foo } = { foo: "aaa", bar: "bbb" };

//变量名和属性名如果不一样，可以这样写
var { foo: baz } = { foo: 'aaa', bar: 'bbb' };
```
字符串解构赋值
```
const [a, b, c, d, e] = 'hello';
```

还可以对数值和布尔值，函数参数解构赋值。

#### Set和Map

**Set**

ES6 提供了新的数据结构 Set。它类似于数组，但是成员的值都是唯一的，没有重复的值。

```
// 例一
var set = new Set([1, 2, 3, 4, 4]);
[...set]
// [1, 2, 3, 4]

// 例二
var items = new Set([1, 2, 3, 4, 5, 5, 5, 5]);
items.size // 5

// 例三
function divs () {
  return [...document.querySelectorAll('div')];
}

var set = new Set(divs());
set.size // 56

// 类似于
divs().forEach(div => set.add(div));
set.size // 56
```
**Map**

JavaScript的对象（Object），本质上是键值对的集合（Hash结构），但是传统上只能用字符串当作键。这给它的使用带来了很大的限制。为了解决这个问题，ES6提供了Map数据结构。它类似于对象，也是键值对的集合，但是“键”的范围不限于字符串，各种类型的值（包括对象）都可以当作键。也就是说，Object结构提供了“字符串—值”的对应，Map结构提供了“值—值”的对应，是一种更完善的Hash结构实现。如果你需要“键值对”的数据结构，Map比Object更合适。

```
var m = new Map();
var o = {p: 'Hello World'};

m.set(o, 'content')
m.get(o) // "content"

m.has(o) // true
m.delete(o) // true
m.has(o) // false
```

#### 字符串模板

传统的JavaScript语言，输出模板通常是这样写的。
```
$('#result').append(
  'There are <b>' + basket.count + '</b> ' +
  'items in your basket, ' +
  '<em>' + basket.onSale +
  '</em> are on sale!'
);
```
ES6是这样解决的
```
$('#result').append(`
  There are <b>${basket.count}</b> items
   in your basket, <em>${basket.onSale}</em>
  are on sale!
`);
```

如果使用模板字符串表示多行字符串，所有的空格和缩进都会被保留在输出之中。
```
$('#list').html(`
<ul>
  <li>first</li>
  <li>second</li>
</ul>
`);
```

同时字符串模板中还可以嵌入变量，变量可以写在${}里面。
```
var x = 1;
var y = 2;

`${x} + ${y} = ${x + y}`
// "1 + 2 = 3"

`${x} + ${y * 2} = ${x + y * 2}`
// "1 + 4 = 5"

var obj = {x: 1, y: 2};
`${obj.x + obj.y}`
// 3
```

字符串模板还支持嵌套
```
const tmpl = addrs => `
  <table>
  ${addrs.map(addr => `
    <tr><td>${addr.first}</td></tr>
    <tr><td>${addr.last}</td></tr>
  `).join('')}
  </table>
`;
const data = [
    { first: '<Jane>', last: 'Bond' },
    { first: 'Lars', last: '<Croft>' },
];

console.log(tmpl(data));
// <table>
//
//   <tr><td><Jane></td></tr>
//   <tr><td>Bond</td></tr>
//
//   <tr><td>Lars</td></tr>
//   <tr><td><Croft></td></tr>
//
// </table>
```

#### 默认值

在以前，我们声明了一个有很多参数的函数时，无法直接指定默认值，所有会很很多default配置来处理。
```
function log(x, y) {
  y = y || 'World';
  console.log(x, y);
}
```
但是这种处理方法是不安全的，如果我们这样赋值
```
log('Hello') // Hello World
log('Hello', 'China') // Hello China
log('Hello', '') // Hello World
```
ES6 允许为函数的参数设置默认值，即直接写在参数定义的后面。
```
function log(x, y = 'World') {
  console.log(x, y);
}

log('Hello') // Hello World
log('Hello', 'China') // Hello China
log('Hello', '') // Hello
```

### rest参数

ES6 引入 rest 参数（形式为“...变量名”），用于获取函数的多余参数，这样就不需要使用arguments对象了。rest 参数搭配的变量是一个数组，该变量将多余的参数放入数组中。

```
function add(...values) {
  let sum = 0;

  for (var val of values) {
    sum += val;
  }

  return sum;
}

add(2, 5, 3) // 10
```
**扩展运算符 ...**

它好比 rest 参数的逆运算，将一个数组转为用逗号分隔的参数序列。
```
console.log(...[1, 2, 3])
// 1 2 3

console.log(1, ...[2, 3, 4], 5)
// 1 2 3 4 5

[...document.querySelectorAll('div')]
// [<div>, <div>, <div>]
```

参考资料
 * http://es6.ruanyifeng.com/
 * http://www.jianshu.com/p/ebfeb687eb70
