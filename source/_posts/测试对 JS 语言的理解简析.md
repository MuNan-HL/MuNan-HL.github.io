---
title: 测试对 JS 语言的理解
date: 2024-8-11
---
这里将会记录常见的 JS 语言的问题, 用于测试你对 JS 语言的理解和掌握程度.  

## JS 语言面试题系列
- [参考资料 讯飞星火](https://xinghuo.xfyun.cn/desk)

- [参考资料 JS 语言面试题系列](https://cchroot.github.io/interview/pages/interview%20questions/js%E5%9F%BA%E7%A1%80%E9%9D%A2%E8%AF%95%E9%A2%98.html)

``` md
> 1. null 空和 undefined 未赋值的区别?
- 1. null 空表示的是一个空对象, 而 undefined 未赋值, 表示的是一个变量已经定义但是未赋值.
```

``` md
> 2. 说说你有什么办法把数组去重？
- 1. 个人常用的是三种方法, 分别是 Set 集合, Map 映射 以及 Object 对象实现数组去重.
```

``` md
> 3. 有写过原生的自定义事件吗？
- 1. JS 原生方法的话, 可以提高 customEvent 自定义事件去自定义一个事件, 然后提高 addEventListener 添加事件监听器去监听事件, 然后通过 dispatchEvent 派发事件去触发事件.

- 2. 代码示例:
```
``` js
// 1.
// let myEvent = new Event('myEvent');
// 2.
// 定义变量 myEvent 存储一个自定义事件
let myEvent = new CustomEvent('myEvent', {
  detail: {
    name: 'lindaidai'
  }
});
// 3.
// let myEvent = document.createEvent('CustomEvent');
// myEvent.initEvent('selfEvent', true, true)

// 定义变量 btn 存储一个 button 按钮元素
let btn = document.getElementsByTagName('button')[0];
// 通过 addEventListener 添加事件监听器去监听事件 
btn.addEventListener('selfEvent', function (e) {
  console.log(e)
  console.log(e.detail)
});

// 设置超时器
setTimeout(() => {
  // 通过 dispatchEvent 派发事件去触发事件 
  btn.dispatchEvent(myEvent)
}, 2000);
```

``` md
> 4. apply 应用, call 调用, bind 绑定三者的相同点及区别
- 1. 首先, apply 应用和 call 调用以及 bind 绑定都是用于指定函数执行上下文的, 主要区别又两个点, 一个是传参格式(是数组还是非数组), 一个函数是否立即执行. apply 应用和 call 调用在第一点上, 传参格式不同, 但是在第二点是一致的, 函数会立即执行. 而 bing 绑定, 在第一点上是和 call 调用一致的, 但是第二点是不同的.

- 2. 个人比较喜欢使用 bind 绑定, 因为函数不会立即执行, 且传参格式为非数组形式, 比较符合习惯.
```

``` md
> 5. 请写出以下代码的输出结果
```
``` js
// 定义一个函数 Person, 接受两个参数 name, sex
function Person (name, sex) {
  // 定义一个公用属性 name
  this.name = name
  // 定义一个公有属性 sex
  this.sex = sex
  // 定义一个私有属性 evil
  var evil = '我是私有属性'
  // 定义一个私有方法 pickNose
  var pickNose = function () {
    console.log('我是私有方法')
  }
  // 定义一个共有方法 drawing
  this.drawing = function () {
    console.log('我是公有方法')  
  }
}
// 定义一个静态方法 fight
Person.fight = function () {
  console.log('我是静态方法')
}
// 定义一个原型方法 protoMethod
Person.prototype.protoMethod = function () {
  console.log('构造函数的原型对象方法')
}
var p1 = new Person('xiaomao', 'cat')
console.log(p1.name)
console.log(p1.evil)
p1.drawing()
p1.pickNose()
p1.fight()
p1.protoMethod()
Person.fight()
Person.protoMethod()
console.log(Person.sex)
```
``` md
- 补充知识1, 公有属性是可以被对象实例访问得到的属性, 静态属性是只能被类自己访问得到的属性, 而私有属性是只能被类内部访问得到的属性.
```

``` md
> 6. CommonJS 通用 JS 语言模块和 ES6 JS 语言标准模块的区别？
- 1. 主要区别就是, 一个多用于服务端编程, 一个多用于客户端编程. 其余区别就是一些语法的不同, 比如导入导出语法不同, this 对象的指向不同, 以及模块加载的阶段不同. 
```

``` md
> 7. 说说回流（重排）和重绘
- 1. 回流, 是指元素的位置样式和尺寸样式发生改变后, 浏览器的渲染引擎会重写进行页面布局和页面绘制. 而重绘, 是指元素的视觉样式发生改变后, 浏览器的渲染引擎会重新执行一次页面绘制过程, 但是并不会重新执行页面布局.

- 2. 浏览器的渲染引擎的执行过程个人觉得主要有四个阶段, 第一阶段是代码解析阶段, 第二阶段是 render 渲染树构建阶段, 第三阶段是页面布局阶段, 第四阶段是页面绘制阶段.
```

``` md
> 8. 在移动端中怎样初始化根元素的字体大小？
- 1. 移动端的问题在于适配问题, 所以推荐使用响应式的尺寸, 比如 em 相对长度单位(读音: /em/)和 rem 根元素相对长度单位(读音: /rem/).

- 2. 代码示例:
```
``` js
// 定义一个函数 setRootFontSize 设置根元素字体大小
function setRootFontSize() {
  const screenWidth = window.innerWidth;
   // 根据屏幕宽度计算并设置根元素的字体大小
  const rootFontSize = screenWidth / 37.5; // 例如，每37.5个像素为1rem，可以根据需要进行调整
  document.documentElement.style.fontSize = rootFontSize + 'px';
}
​
// 在窗口大小改变时调用设置根元素字体大小的函数
window.addEventListener('resize', setRootFontSize);
​
// 页面加载完成后初始化设置根元素字体大小
window.addEventListener('DOMContentLoaded', setRootFontSize);
```

``` md
> 9. animation 动画有一个 steps() 步骤功能符知道吗？
- 1. animation 动画中的 steps 步骤, 可以实现动画的不连续.

- 2. 首先, animation 动画是 CSS 层叠样式的一个样式规则, 我们可以通过 animation 动画实现将 @keyframes 关键帧绑定在指定元素上, 进而实现动画的效果. 
```

``` md
> 10. 在项目中如何把 http 超文本传输协议的网络请求换成 https 超文本传输协议安全版的网络请求?
- 1. 在 Vue Web 网站前端框架下, 我是通过二次封装 axios 网络请求库实现的转换. 通过设置网络请求的 baseURL 基本统一资源定位符.
```

``` md
> 11. requestAnimationFrame 请求动画帧有了解过吗？
- 1. requestAnimationFrame 全球动画帧用于实现更平滑的动画效果.

- 2. 代码示例:
```
``` js
// 定义一个函数 animate 动画
function animate() {
  // 在这里编写动画逻辑
  // ...

  // 请求下一帧动画, 将 animate 动画函数递归
  requestAnimationFrame(animate);
}

// 启动动画循环
requestAnimationFrame(animate);
```

``` md
> 12. 平常工作中 ES6+ 标准+ 中主要用到了哪些？
- 1. 异步编程, 模块的导入导出, 箭头函数, 异常捕获, 扩展操作符, 解构 ... 等等, 其余具体的内容记不清了. 
```

``` md
> 13. 如何判断一个变量是对象还是数组？
- 1. 我是通过 toString 转化为字符串方法实现的.

- 2. 代码示例:
```
``` js
function isObjArr(value){
  if (Object.prototype.toString.call(value) === "[object Array]") {
    console.log('value是数组');
  }else if(Object.prototype.toString.call(value)==='[object Object]'){//这个方法兼容性好一点
    console.log('value是对象');
  }else{
    console.log('value不是数组也不是对象')
  }
}
```

``` md
> 14. 通过 reduce 简化来实现简单的数组求和，示例数组[3,4,8,0,9];
- 1. 首先, reduce 简化, 是用来遍历数组的, 它的参数是一个回调函数, 该函数可以接受四个参数, 返回值是按照返回条件返回的.

- 2. 代码示例:
```
``` js
let result = [3,4,8,0,9].reduce((accumulator, item, index, array)=>{
	return accumulator + item;
});
```

``` md
> 15. 以下代码的输出结果
```
``` js
// 定义一个函数 foo
function foo () {
  // 输出 this 对象的 a 变量 
  console.log(this.a)
};
// 定义一个变量 obj
var obj = { a: 1, foo };
// 定义一个变量 a
var a = 2;
// 定义一个变量 foo2
var foo2 = obj.foo;
// 定义一个变量 obj2
var obj2 = { a: 3, foo2: obj.foo }

// 执行 obj 对象中的 foo 函数
obj.foo(); // 1
// 执行 foo2 函数
foo2(); // 2
// 执行 obj2 对象中的 foo2 函数
obj2.foo2(); // 3
```

``` md
> 16. 如何添加、删除、移动、复制 DOM 文档对象模型的节点
- 1. 通过 createElement 创建元素去创建一个元素, 通过 appendChild 追加孩子去追加元素, 通过 removeChild 移除孩子去移除元素, 通过 replaceChild 替换元素去替换元素. 通过 getElementsByClassName 通过类名获取元素去获取元素, 通过 querySelector 查询选择器去查询元素. 通过 cloneNode 克隆节点去克隆元素.
```

``` md
> 17. DOM 文档对象模型的事件中 target 目标和 currentTarget 当前目标的区别?
- 1. target 目标表示的是第一次触发该事件的元素, currentTarget 当前目标表示的是第一次监听该事件的元素. 需要注意的是, 由于事件冒泡机制, 所以 target 目标和 currentTarget 当前目标有时候是同一个元素, 有时候不是. 

- 2. 代码示例:
```
``` js
<body>
   <ul id="box">
      <Li id="apple">苹果</Li>
      <li>香蕉</li>
      <li>桃子</li>
   </ul>
</body>
<script>
  const box = document.getElementById('box');
  const apple = document.getElementById('apple');

  //直接绑定在目标元素apple上
  apple.onclick = function (e){  
    console.log(e.target);          //<li id="apple">苹果</li>
    console.log(e.currentTarget);    //<li id="apple">苹果</li>
    console.log(this);               //<li id="apple">苹果</li>
    console.log(e.target === e.currentTarget);      //true
    console.log(e.target === this);           //true
  } 

  //绑定在父元素box上（如果点击apple这个li时）
   box.onclick = function (e){
      console.log(e.target);           // <li id="apple">苹果</li>
      console.log(e.currentTarget);       //<ul id="box">...</ul>
      console.log(this);                  //<ul id="box">...</ul>
      console.log(e.currentTarget===this);      //true
      console.log(e.target === e.currentTarget);        //false
      console.log(e.target === this);           //false
   }
</script>
```

``` md
> 18. 说一下 let 变量、const 常量、var 变量的区别和 let 变量、const 常量的暂时性死区
- 1. 区别就是, ES5 JS 语言标准之后出现了 let 变量 和 cosnt 常量关键字, 解决了 var 变量存在的变量提升问题.
然后, 暂时性死区就是因为没有了变量提升, 从而导致在未定义变量之前会无法调用该变量.
```

``` md
> 19. Map 映射, Set 集合、WeakMap 弱映射，什么作用【描述】
- 1. Map 映射, Set 集合 以及 WeakMap 弱映射, 都是引用数据类型, Map 映射多用于做字典, Set 集合多用于数组去重, WeakMap 弱映射多用于防止内存泄漏.
```

``` md
> 20. 以下代码将会输出什么，解释以下
```
``` js
let n = [10, 20];
let m = n;
let x = m;
m[0] = 100;
x = [30, 40];
x[0] = 200;
m = x;
m[1] = 300;
n[2] = 400;
console.log(n, m, x) 

// [100, 20, 400]
// [200, 300]
// [200, 300]
```

``` md
> 21. 下面这段代码输出结果是什么?
```
``` js
const arr = [1,2,3,4,5,6]
arr.forEach(async (item) => {
  await sleep(item)
  console.log('after', item)
})
function sleep(item){
  return new Promise(res => {
    setTimeout(() => {
        res(console.log('before', item))
    }, 2000)
  })
}

/*
before 1
after 1
before 2
after 2
before 3
after 3
before 4
after 4
before 5
after 5
before 6
after 6
*/
```

``` md
> 22. 写出代码输出值，并说明原因
```
``` js
function F() {
  this.a = 1;
}
var obj = new F();
console.log(obj.prototype); // undefined
```
``` md
- 1. 对象实例的 prototype 原型对象, 需要显示的设置其 __proto__ 原型属性. 如果你直接访问一个对象的原型对象，而该对象并没有显式地设置其原型，那么它的原型对象将是undefined
```

``` md
> 23. weak-Set 弱集合、weak-Map 弱映射 和 Set 集合、Map 映射的区别？
- 1. Set 集合：Set 集合是一种无序且不重复的数据结构，它只存储唯一的值。可以使用 add 新增去添加元素，使用 delete 删除去删除元素，使用 has 包含去检查元素是否存在。
```
``` js
const mySet = new Set();
mySet.add(1);
mySet.add(2);
mySet.add(3);
console.log(mySet.has(1)); // true
mySet.delete(1);
console.log(mySet.has(1)); // false
```
``` md
- 2. Map 映射：Map 映射是一种键值对的集合，它的键可以是任意类型的值（对象、原始值等），而不仅仅是字符串或符号。与 Set 集合类似，Map 映射中的 key 键也是唯一的。可以使用 set 设置去添加键值对，使用 get 获取去获取键对应的值，使用 has 包含去检查键是否存在，使用 delete 删除去删除键值对。
```
``` js
const myMap = new Map();
myMap.set('key1', 'value1');
myMap.set('key2', 'value2');
console.log(myMap.get('key1')); // 'value1'
myMap.delete('key1');
console.log(myMap.has('key1')); // false
```
``` md
- 3. Weak-Set 弱集合：Weak-Set 若集合是 Set 集合的一种，区别在于它的成员 value 值只能是对象，并且这些对象都是弱引用的。这意味着如果没有其他引用指向这些对象，它们会被垃圾回收机制回收。Weak-Set 不能遍历，也没有 size 大小属性。
```
``` js
const weakSet = new WeakSet();
const obj1 = {};
const obj2 = {};
weakSet.add(obj1);
weakSet.add(obj2);
console.log(weakSet.has(obj1)); // true
obj1 = null; // 移除 obj1 的引用
console.log(weakSet.has(obj1)); // false
```
``` md
- 4. Weak-Map 弱映射：Weak-Map 弱映射是 Map 映射的一种，它的 key 键必须是对象，并且这些对象都是弱引用的。与 Weak-Set 弱集合类似，如果没有其他引用指向这些对象，它们会被垃圾回收机制回收。Weak-Map 弱映射同样不能遍历，也没有 size 大小属性。
```
``` js
const weakMap = new WeakMap();
const key1 = {};
const key2 = {};
weakMap.set(key1, 'value1');
weakMap.set(key2, 'value2');
console.log(weakMap.get(key1)); // 'value1'
key1 = null; // 移除 key1 的引用
console.log(weakMap.get(key1)); // undefined
```

``` md
> 24. ['1', '2', '3'].map(parseInt) what & why ?
- 1. map 映射, 一种遍历数组的方法, 会接受一个回调函数, 并根据 return 返回条件, 返回一个数组.

- 2. parseInt 解析整数, 会接受一个 String 字符串和一个 radix 基数, 并返回一个的整数. 
```

``` md
> 25. 如何正确判断 this 当前对象的指向？
- 1. this 对象的指向, 会指向当前调用者. 即谁调用则指向谁.
```

``` md
> 26. 说一说你对 JS 语言的执行上下文栈和作用域链的理解？
- 1. 要了解执行上下文栈, 就需要了解 JS 引擎的执行过程.

- 2. JS 引擎的执行过程, 大致分为三个阶段, 首先是语法分析阶段(进行 JS 语言的语法分析, 如果语法出错则会抛出 syntaxError 语法异常.), 
然后是预编译阶段(会创建执行上下文), 最后是执行阶段(即事件循环机制, 通过执行上下文栈, 任务队列以及 Web API 网站应用程序接口实现).

- 3. JS 语言中的作用域链, 首先, 是静态作用域链, 即作用域链在函数定义时已经确定. 其次, 作用域链是一种查找机制, 通过作用域链一层层向上寻找某个变量, 直到找到全局作用域还是没找到，则会抛出 referenceError 引用异常, not defined 未定义。 
```
- [参考资料 JS 引擎的执行过程](https://heyingye.github.io/2018/03/19/js%E5%BC%95%E6%93%8E%E7%9A%84%E6%89%A7%E8%A1%8C%E8%BF%87%E7%A8%8B%EF%BC%88%E4%B8%80%EF%BC%89/)

``` md
> 27. 可迭代对象有哪些特点
- 1. 实现了 iterator 迭代器的对象, 就是可迭代对象. 一个可迭代对象可以通过 for in 循环去遍历该对象, 且可以通过 spread 扩展运算符去展开该对象.

- 补充知识1, 可以通过 typeof 类型检测去检测该对象中是否存在 iterator 迭代器.
```
``` js
function isIterable(obj) {
  return obj != null && typeof obj[Symbol.iterator] === 'function';
}

console.log(isIterable([1, 2, 3])); // true
console.log(isIterable('hello')); // true
console.log(isIterable(new Map())); // true
console.log(isIterable(new Set())); // true
console.log(isIterable({})); // false
console.log(isIterable(42)); // false
```

``` md
> 28. sum(2, 3) 实现 sum(2)(3) 的效果
- 1. 通过柯里化函数实现.
```

``` md
> 29. Promise 期约和 Callback 回调有什么区别?
- 1. Promise 期约和 callback 回调是两种实现异步编程的机制, 现在更推荐使用 async\await 异步等待去实现异步编程. 不推荐使用 callback 回调的原因是, 回调地狱导致的代码不可维护的问题. 不推荐 Promise 期约的问题是, 虽然 Promise 期约有链式调用可以解决回调地狱的问题, 但是当链式调用很多层后, 但是使得代码难以维护, 而此时的 async/await 异步等待, 解决了这个问题.
```

``` md
> 30. 实现图片懒加载的思路
- 1. 整体就是三步, 首先确定可视区域, 然后监听图片是否到达可视区域, 最后进行图片加载.

- 2. 什么是图片懒加载?(图片懒加载是一种优化网页性能的技术，它的主要思路是在页面滚动到图片位置时再加载图片，而不是一开始就加载所有图片。)
```

``` md
> 31. 表单可以跨域吗？
- 1. 首先, 表单本身是不涉及跨域, 你会产生跨域, 是因为你去提交表单数据时发送的网络请求而导致的. 

- 补充知识1, 首先跨域, 是指域名A的网页去请求域名B的资源, 由于浏览器的同源策略导致的请求失败.
```

``` md
> 32. 为什么 typeof 类型检测可以检测类型，有没有更好的方法
- 1. 这个问题通过 typeof 的底层实现可以简单了解, typeof 底层是通过二进制的1 和 0 的位数决定该变量是何种数据类型的. 这也解释了, 为什么 typeof 类型检查会认为 null 空是 Object 对象.

- 2. 更好的检测变量类型的方法, 代码示例
```
``` js
const arr = [1, 2, 3];
const isArray = Object.prototype.toString.call(arr) === '[object Array]';
console.log(isArray); // 输出 true

function testFunc() {}
const isFunction = Object.prototype.toString.call(testFunc) === '[object Function]';
console.log(isFunction); // 输出 true
```

``` md
> 33. 什么是事件委托，它有什么好处？
- 1. 事件委托是事件冒泡的最佳实践. 通过只在父级元素上去监听事件, 节省了资源(内存资源)又提升了性能(减少 DOM 文档对象模型的操作).

- 2. 事件冒泡是一种事件传播机制, 由内向外. 
```

``` md
> 34. 使用 js 语言如何改变 url 统一资源定位符，并且页面不刷新？
- 1. 第一种是通过 hash 哈希模式实现, 第二种是通过 history 历史模式实现.
```

``` md
> 35. 实现一个方法，用于比较两个版本号（version1 版本1, version2 版本2）
```

``` md
> 36. 浏览器为什么要阻止跨域请求？如何解决跨域？每次跨域请求都需要到达服务端吗？
- 1. 浏览器的同源策略, 本质还是为了网络安全. 比如一个恶意网站的页面通过 iframe 内联框架嵌入了银行的登录页面（二者不同源），如果没有同源限制，恶意网页上的 javascript 语言脚本就可以在用户登录银行的时候获取用户名和密码。
```

``` md
> 37. 深拷贝实现
- 1. 递归实现
```
``` js
// 递归拷贝
function deepClone(obj, hash = new WeakMap()) {
  if (obj instanceof RegExp) return new RegExp(obj)
  if (obj instanceof Date) return new Date(obj)
  if (obj === null || typeof obj !== 'object') {
	// 如果不是复杂数据类型，直接返回	
    return obj
  }
  if(hash.has(obj)) {
	// 如果已经处理过相同的对象，直接获取（解决循环引用）
	return hash.get(obj)
  }
  /**
   * 如果 obj 是数组，那么 obj.constructor 是 [Function: Array]
   * 如果 obj 是对象，那么 obj.constructor 是 [Function: Object]
   */
  let t = new obj.constructor()
  hash.set(obj, t)
  for (let ikey in obj) {
	// 递归
	if (obj.hasOwnProperty(key)) { // 是否是自身的属性
	  t[key] = deepClone(obj[key], hash)
	}  
  }
}
```

``` md
> 38. 深拷贝怎么解决循环引用问题
```

``` md
> 39. 编写一个程序将数组扁平化去并除其中重复部分数据，最终得到一个升序且不重复的数组
- 1. 代码示例
```
``` js
Array.from(new Set(arr.flat(Infinity))).sort((a,b)=>{ return a-b});
```

``` md
> 40. 描述一下 Promise 期约
- 1. Promise 期约, 本质是一个对象, 一个用来表示异步操作是 fulfilled 已兑现还是 rejected 已拒绝的对象. 其可以进行链式调用.
```

``` md
> 41. 如何实现大文件上传？
- 1. 本质是通过切片上传(前端三步, 1. 文件切片, 2. 上传切片, 3. 发送合并请求; 后端 2 步, 1. 接受切片, 2. 合并切片)

- 补充知识1. 断点续传(由于某种原因导致文件上传失败或者暂停, 因此需要记住已经上传成功的切片, 以便继续上传后续的切片.)
```

``` md
> 42. 表单可以跨域么？
- 1. 首先, 表单和跨域没有直接联系, 产生跨域的原因在于, 提交表单时发送的网络请求产生了跨域.
```

``` md
> 43. 观察者模式和订阅-发布模式的区别，各⾃⽤在哪⾥？
- 1. 观察者模式是一种一对多的依赖关系. 通常一个 subject 主题会依赖于多个 observer 观察者, 并在 subject 主题发生变化后通知 observer 观察者, 观察者会并根据自身需求更新. 优点在于松耦合, 缺点在于可能会存在循环依赖(`即双向依赖, 具体来说，就是观察者模式中的主题（Subject）维护了一个观察者列表，当主题的状态发生变化时，它会通知所有的观察者。观察者在接收到通知后，可能需要访问主题的状态来做出相应的更新。这就导致了观察者和主题之间的双向依赖关系。`)且当观察者过多后, 会导致性能下降的问题.

- 2. 发布-订阅模式是一种消息传递范式, 消息的发布方会把消息发布到 channel 频道中, 然后消息的订阅方会从 channel 频道中订阅所需的消息. 因此发布方和订阅方之间没有直接的关联，它们是通过中间件进行的通信. 优点是实现了发布方和订阅方的解耦, 缺点在于要维护 channel 频道中的消息.

- 3. 对于观察者模式和发布订阅模式的取舍, 取决于你的实际需求, 如果只是单纯的一对多的依赖关系, 那么观察者模式就OK了, 但是如果为了灵活的传递消息, 更推荐发布订阅模式.
```

``` md
> 44. 简单介绍下 AST 抽象语法树
- 1. AST 抽象语法树是对源代码的抽象表示, 即用一个树型结构表示源代码, 常用于分析、转换和生成代码.

- 2. AST 抽象语法树的构建过程通常包括以下 3 步, 1. 词法分析, 语法分析, 语义分析. 
```

``` md
> 45. 如何将 AST 抽象语法树转换为中间代码或目标代码?
```

``` md
> 46. js 语言的定时器为什么是不精确的?
- 1. 因为 JS 语言中的定时器是一个异步任务, 因此必然会存在不精确的问题.
```