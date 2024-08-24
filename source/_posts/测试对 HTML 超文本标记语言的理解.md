---
title: 测试对浏览器的理解简析
date: 2024-8-22
---
这里将会记录 HTML 超文本标记语言的相关面试题目, 用于测试你对 HTML 超文本标记语言的理解.

- [参考资料 讯飞星火](https://xinghuo.xfyun.cn/desk)

- [参考资料 HTML 超文本标记语言面试题系列](https://juejin.cn/post/6905294475539513352#heading-0)

``` md
> 1. src 资源和 href 超链接引用的区别 
- 1. src 资源指的是外部资源, 用于引入外部资源, 而 href 超链接引用指的是一个超链接, 用于链接到外部资源的.
```

``` md
> 2. 对 HTML 超文本标记语言语义化的理解
- 1. HTML 超文本标记语言语义化就是指, 给每个元素不同的含义, 用于做不同的事情. 优点在于代码的可维护性以及良好的 SEO 搜索引擎优化, 有利于爬虫爬取数据.
```

``` md
> 3. DOCTYPE ⽂档类型的作⽤
- 1. DOCTYPE 文档类型, 用于定义当前文档的类型, 告诉浏览器用什么样的文档类型定义来解析文档.(html 超文本标记语言或 xhtml 扩展的超文本标记语言)
```

``` md
> 4.  script 脚本标签中 defer 延迟和 async 异步的区别
- 1. 首先, defer 延迟和 async 异步, 是用于控制 JS 语言的加载和执行顺序的方法. `其中 defer 延迟, 会延迟 JS 语言的执行`, 即会在加载完 JS 语言后, 等待 HTML 超文本标记语言的解析, 最后在运行 JS 语言. 而 async 异步, 不会延迟 JS 语言的延迟, 即会在加载完 JS 语言后, 立即执行 JS 语言文件, 最后在解析剩余的 HTML 超文本标记语言.

- 补充知识1, 需要注意的是，async 异步和 defer 延迟不能同时使用. 如果两者都存在，defer 延迟会被忽略.
```

``` md
> 5. 常⽤的 meta 元标签有哪些
- 1. 首先 meta 元元素, 是用来描述文档内容的元素, 所以 meta 元元素可以用来描述文档的 charset 字符集, keywords 关键字, description 描述, 以及 refresh 刷新, 和 viewport 视口.

- 补充知识1, meta 需要搭配 content 内容属性一起使用.
```
``` html
<meta charset="UTF-8" >
<meta name="keywords" content="关键词" />
<meta name="description" content="页面描述内容" />
<meta http-equiv="refresh" content="0;url=" />
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1">
<meta name="robots" content="index,follow" />
```

``` md
> 6. HTML5 超文本标记语言有哪些更新
- 1. 我比较常用的有 4 个, 分别是`元素语义化, 媒体元素, 表单元素, 以及网站存储等`. 
```

``` md
> 7. img 图像的 srcset 资集合属性的作⽤？
- 1. srcset 资集合是 img 图像的一个属性, 可以提供一组图像, 以便浏览器根据不同条件自动选择最合适的图像.
```
``` html
<!-- 根据像素密度做区分 -->
<img srcset="foo-320w.jpg,
             foo-480w.jpg 1.5x,
             foo-640w.jpg 2x"
     src="foo-640w.jpg">

<!-- 根据屏幕大小做区分 -->
<img srcset="foo-160.jpg 160w,
             foo-320.jpg 320w,
             foo-640.jpg 640w,
             foo-1280.jpg 1280w"
     src="foo-1280.jpg">

<!-- 搭配 size 大小一起使用 -->
<img srcset="foo-160.jpg 160w,
             foo-320.jpg 320w,
             foo-640.jpg 640w,
             foo-1280.jpg 1280w"
     sizes="(max-width: 440px) 100vw,
            (max-width: 900px) 33vw,
            254px"
     src="foo-1280.jpg">

<!-- 像素密度 + 屏幕大小 -->
<picture>
  <source srcset="homepage-person@desktop.png,
                  homepage-person@desktop-2x.png 2x"       
          media="(min-width: 990px)">
  <source srcset="homepage-person@tablet.png,
                  homepage-person@tablet-2x.png 2x" 
          media="(min-width: 750px)">
  <img srcset="homepage-person@mobile.png,
               homepage-person@mobile-2x.png 2x" 
       alt="Shopify Merchant, Corrine Anestopoulos">
</picture>
```
- [参考资料 srcset 资源设置](https://www.ruanyifeng.com/blog/2019/06/responsive-images.html)

``` md
> 8. 行内元素有哪些？块级元素有哪些？ 空(void)元素有那些？
- 1. 首先, 行内元素的有 span 行内元素, a 链接元素, img 图像元素, input 输入框元素等 , 块级元素有 div 块级元素, 文本类元素以及列表元素等, 空元素就是指那些内容为空的元素.
```

``` md
> 9. 说一下 web worker 网站后台线程
- 1. `worker 后台线程, 允许主线程创建 worker 后台线程`, 将一些任务分配给后者运行, 用于解决 JS 语言单线程的问题. 使得在主线程运行的同时, Worker 后台线程在后台运行, 两者互不干扰. 等到 Worker 后台线程完成计算任务, 再把结果返回给主线程. 这样的好处是, 一些计算密集型或高延迟的任务, 被 Worker 后台线程负担了, 主线程（通常负责 UI 交互）就会很流畅, 不会被阻塞或拖慢. 主线程和后台线程之间通过 postMessage 发送消息来发送消息, 通过 onMessage 监听消息来监听消息. `相较于主线程, worker 后台线程的通信和可获取的数据是受限`
```
- [参考资料 worker 后台线程](https://www.ruanyifeng.com/blog/2018/07/web-worker.html)

``` md
> 10.  HTML5 超文本标记语言的离线储存怎么使用，它的工作原理是什么
- 1. 简单来说就是新建一个 .appcache 应用程序缓存文件, 后期通过和该文件进行通信, 实现离线存储.

- 补充知识1, 浏览器是如何对 HTML5 的离线储存资源进行管理和加载？
```

``` md
> 11. title 标题与 h1 一级标题的区别、b 加粗与 strong 强调的区别、i 斜体与 em 斜体的区别？
- 1. 区别主要是两个地方, 一个是语义上的不同, 一个是对 SEO 搜索引擎优化的影响不同.
```

``` md
> 12.  iframe 内联框架有那些优点和缺点？
- 1. `iframe 内联框架可以让你在一个网页中嵌入另一个网页`. 所以优点就是 iframe 内联框架能够原封不动的把嵌入的网页展现出来, 比如你在网页中看到的广告. 缺点也很明显, 就是会产生很多页面, 不容易管理, 如果框架个数多的话, 可能会出现上下, 左右滚动条, 会分散访问者的注意力, 用户体验度差. 所以 iframe 内联框架的使用次数需要要做限制.
```

``` md
> 13. label 标签的作用是什么？如何使用？
- 1. label 标签是 HTML 超文本标记语言的一个原生元素, 主要是和表单控件搭配使用的. 但是如果你使用像是 Vue, React 网站前端框架之类的网站前端框架的话, 一般是不会用到 label 标签这一原生元素的. 
```

``` md
> 14. Canvas 画布和 SVG 可伸缩矢量图的区别
- 1. Canvas 画布是基于像素进行渲染的, 而 SVG 可伸缩矢量图是基于矢量图形进行渲染的, 因此 SVG 可伸缩矢量图形适合绘制复杂的图形, 保证其不会失真, 而 Canvas 画布则更适合用于网站游戏和动画的绘制.
```

``` md
> 15. head 头部元素有什么作用，其中什么标签必不可少？
- head 头部元素, 是用于定义 HTML 超文本标记语言文档的头部数据的, 比如 title 标题, meta 元元, style 样式, script 脚本...等.
```

``` md
> 16. 文档声明（Doctype）和<!Doctype html>有何作用? 严格模式与混杂模式如何区分？它们有何意义?
- 1.`Doctype 文档声明, 用于定义文档的类型的, 告诉浏览器当前 HTML 超文本标记语言文档使用什么版本的 HTML 超文本标记语言来写的`，这样浏览器才能按照声明的版本来正确的解析. 最佳实践是 <!Doctype html>, 告诉浏览器当前的文档是 HTML5 超文本标记语言第五版文档.
```

``` md
> 17. 渐进增强和优雅降级之间的区别
- 1.  渐进增强和优雅降级的区别主要体现在 CSS 层叠样式表的书写格式上, 是渐进增强是先写低级样式在写高级样式, 优雅降级则相反. 目的是对不同版本的浏览器的适配.
```

``` md
> 18. 浏览器乱码的原因是什么？如何解决？
- 1. 浏览器出现乱码, 肯定是因为你的编码格式的问题.比如 GBK 国标扩展和 UTF-8 通用字符集, 其中的 8, 表示的是它使用 8 位一个字节来表示每个符号.
```
- [参考资料 编码格式](https://cloud.tencent.com/developer/article/1460395)