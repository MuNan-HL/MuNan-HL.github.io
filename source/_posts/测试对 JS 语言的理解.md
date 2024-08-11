---
title: 测试对 JS 语言的理解
date: 2024-8-11
---
这里将会记录常见的 JS 语言的问题, 用于测试你对 JS 语言的理解和掌握程度. 

## JS 语言面试题系列
- [参考资料 讯飞星火](https://xinghuo.xfyun.cn/desk)

- [参考资料 JS 语言面试题系列](https://cchroot.github.io/interview/pages/interview%20questions/js%E5%9F%BA%E7%A1%80%E9%9D%A2%E8%AF%95%E9%A2%98.html)

``` md
> 1. null 空和 undefined 未定义的区别?
```

``` md
> 2. 说说你有什么办法把数组去重？
```

``` md
> 3. 有写过原生的自定义事件吗？
```

``` md
> 4. apply 应用, call 调用, bind 绑定三者的相同点及区别
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
```

``` md
> 7. 说说回流（重排）和重绘
```

``` md
> 8. 在移动端中怎样初始化根元素的字体大小？
```

``` md
> 9. animation 动画有一个 steps() 步骤功能符知道吗？
```

``` md
> 10. 在项目中如何把 http 超文本传输协议的网络请求换成 https 超文本传输协议安全版的网络请求?
```

``` md
> 11. requestAnimationFrame 请求动画帧有了解过吗？
```

``` md
> 12. 平常工作中 ES6+ 标准+ 中主要用到了哪些？
```

``` md
> 13. 如何判断一个变量是对象还是数组？
```

``` md
> 14. 通过 reduce 归并函数来实现简单的数组求和，示例数组[3,4,8,0,9];
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
```

``` md
> 17. DOM 文档对象模型的事件中 target 目标和 currentTarget 当前的区别?
```

``` md
> 18. 说一下 let 变量、const 常量、var 变量的区别和 let 变量、const 常量的暂时性死区
```

``` md
> 19. Map 映射, Set 集合、WeakMap 弱映射，什么作用【描述】
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
> 23. weak-Set 弱集合、weak-Map 弱映射 和 Set 集合、Map 映射的区别？
```

``` md
> 24. ['1', '2', '3'].map(parseInt) what & why ?
```

``` md
> 25. 如何正确判断 this 当前对象的指向？
```

``` md
> 26. 说一说你对 JS 语言的执行上下文栈和作用域链的理解？
```

``` md
> 27. 可迭代对象有哪些特点
```

``` md
> 28. sum(2, 3) 实现 sum(2)(3) 的效果
```

``` md
> 29. Promise 期约和 Callback 回调有什么区别?
```

``` md
> 30. 实现图片懒加载的思路
```

``` md
> 31. 表单可以跨域吗？
```

``` md
> 32. 为什么 typeof 类型可以检测类型，有没有更好的方法
```

``` md
> 33. 什么是事件委托，它有什么好处？
```

``` md
> 34. 使用 js 语言如何改变 url 统一资源定位符，并且页面不刷新？
```

``` md
> 35. 实现一个方法，用于比较两个版本号（version1 版本1, version2 版本2）
```

``` md
> 36. 浏览器为什么要阻止跨域请求？如何解决跨域？每次跨域请求都需要到达服务端吗？
```

``` md
> 37. 深拷贝实现
```

``` md
> 38. 深拷贝怎么解决循环引用问题
```

``` md
> 39. 编写一个程序将数组扁平化去并除其中重复部分数据，最终得到一个升序且不重复的数组
```

``` md
> 40. 描述一下 Promise 期约
```

``` md
> 41. 如何实现大文件上传？
```

``` md
> 42. 表单可以跨域么？
```

``` md
> 43. 观察者和订阅-发布的区别，各⾃⽤在哪⾥？
```

``` md
> 44. 简单介绍下 AST 抽象语法树
```

``` md
> 45. 如何将 AST 抽象语法树转换为中间代码或目标代码?
```

``` md
> 46. js 语言的定时器为什么是不精确的?
```