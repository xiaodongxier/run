# 面试机会


## [聚英翱翔](https://www.zhipin.com/job_detail/4b07a0d8d8ef47241XB_2ti-E1JV.html) / 面试 / 20230307 

### 职位要求

1、全日制公办统专科及以上学历（学信网可查），1年或以上的开发经验
2、精通JavaScript，具备一定框架设计能力，有桌面端，移动端H5开发经验；
3、精通html5 css3，具备页面重构能力；
**4、熟练掌握 Vue2、uni-app;**
**5、熟练掌握canvas、svg；**
**6、熟悉Vue3、WebSocket优先；**
7、熟悉应用threejs优先，可考虑加薪。
8、有一定的思维逻辑能力，可完成页面数据加工处理。
9、有3个独立项目以上的经验。
10、熟悉Android、IOS打包发布。
11、积极乐观，责任心强，工作认真细致，具备良好的交付意识，具有良好的团队沟通与协作能力。
12、当前职位侧重于js编程能力，需要有一定的低代码开发框架能力 或者  需要一定的软件架构思想 或者 后台开发经验。
13、当前工作需要完成基于threejs和svg编程的低代码页面开发平台， 需要关联物联网设备数据，是否愿意挑战此工作？

### 职位要求复习

1. HTML5 
   1. 什么是HTML5？
      1. HTML5是最新的HTML标准，它的主要目标是提供所有内容，而不需要任何Flash、 SilverLight等的额外插件，这些内容来自动画、视频、富GUI等
   2. [HTML5有哪些新特性？移除了哪些元素？](https://blog.csdn.net/CSDNWuZhiChun/article/details/119543376)
   3. 如何区别HTML和HTML5？
      1. 用 DOCTYPE声明新增的结构元素和功能元素来区别它们。
   4. HTML5 Canvas元素有什么作用？
      1. Canvas元素用于在网页上绘制图形，该元素标签的强大之处在于可以直接在HTML上进行图形操作。
   5. HTML5的离线存储有哪些？
      1. 有以下离线存储localStorage，可长期存储数据，即浏览器关闭后数据不丢失，session Storage，数据在浏览器关闭后自动删除
   6. HTML5引入了哪些新的表单属性？
      1. 新增表单属性包括 datalist、 datetime、 output、 keygen、date、 month、week、time、 number、 range、 emailurl
   7. 与HTML4比较，HTML5废弃了哪些元素？
      1. 废弃的元素包括 frame、frameset、 noframe、 applet、big、 center和 basefont。
   8. WebSocket的作用？
      1. 它是Web应用程序的传输协议，提供了双向的、按序到达的数据流。它是HTML5新増的协议， WebSocket的连接是持久的，它在客户端和服务器之间保持双工连接，服务器的更新可以及时推送到客户端，而不需要客户端以一定的时间间隔去轮询。
   9. 如何实现浏览器内多个标签页之间的通信？
      1. 在标签页之间，调用 localstorge、 cookies等数据存储，可以实现标签页之间的通信
   10. 请描述一下 sessionStorage和 localStorage的区别。
       1. sessionStorage用于在本地存储一个会话中的数据，这些数据只有同一个会话中的页面才能访问，当会话结束后，数据也随之销毀。因此 sessionStorage不是一种持久化的本地存储，仅仅是会话级别的存储。
       2. 而 localstorage用于持久化本地存储，除非主动删除数据，否则数据是永远不会过期的。
   11. localStorage和 cookie的区别是什么？
       1. localStorage的概念和cookie相似，区别是 localStorage是为了更大容量的存储设计的。cookie的大小是受限的，并且每次请求一个新页面时， cookie都会被发送过去，这样无形中浪费了带宽。另外， cookie还需要指定作用域，不可以跨域调用。
       2. 除此之外， localStorage拥有 setlten, getItem、 removeltem、 clear等方法， cookie则需要前端开发者自己封装 setCookie和 get Cookie。但 cookie也是不可或缺的，因为 cookie的作用是与服务器进行交互，并且还是HTP规范的一部分，而 localStorage仅因为是为了在本地“存储”数据而已，无法跨浏览器使用。
    12. 请你谈谈 cookie的特点。
        1.  cookie虽然为持久保存客户端数据提供了方便，分担了服务器存储的负担，但是有以下局限性。
        2. 每个特定的域名下最多生成20个 cookie。
        3. IE6或更低版本最多有20个 cookie。
        4. IE7和之后的版本最多可以有50个 cookie。
        5. Firefox最多可以有50个 cookie。
        6. Chrome和 Safari没有做硬性限制。
        7. cookie最大为4096字节，为了兼容性，一般不能超过4095字节。
    13. Cookie和 session的区别是什么？
        1.   cookie数据存放在客户的浏览器上， session数据存放在服务器上。
        2.   cookie不是很安全，别人可以分析存放在本地的 cookie并进行 cookie欺骗。考虑到安全问题应当使用 session。
        3.    session会在一定时间内保存在服务器上。当访问增多时，会占用较多服务器的资源。为了减轻服务器的负担，应当使用 cookie
        4.    单个 cookie保存的数据不能超过4KB，很多浏览器都限制一个站点最多保存20个 cookie
        5.    所以个人建议可以将登录信息等重要信息存放在 session中，其他信息（如果需要保留）可以存放在 cookie中。
    14. 什么是SVG？
        1.  SVG即可缩放失量图形（ Scalable Vector Graphics）。它是基于文本的图形语言，使用文本、线条、点等来绘制图像，这使得它轻便、显示迅速。
    15. Canvas和SvG的区别是什么？
        1.  一旦 Canvas绘制完成将不能访问像素或操作它；任何使用SVG绘制的形状都能被记忆和操作，可以被浏览器再次显示
        2.  Canvas对绘制动画和游戏非常有利；SVG对创建图形（如CAD）非常有利。
        3.  因为不需要记住以后事情，所以 Canvas运行更快；因为为了之后的操作，SVG需要记录坐标，所以运行比较缓慢
        4.  在 Canvas中不能为绘制对象绑定相关事件；在SVG中可以为绘制对象绑定相关事件
        5.  Canvas绘制出的是位图，因此与分辨率有关；SvG绘制出的是矢量图，因此与分辨率无关。
    16. 如何使用 Canvas和HTML5中的SVG画一个矩形？
        1.  使用SVG绘制矩形的代码如下：
          ```html
          <svg xmlns=http://www.w3.org/2000/svg  version="1.1">
          <rect style="fill:rgb（255,100，0）；"height=200"  width="400"></rect>
          </svg>
          ```
        2. 使用 Canvas绘制矩形的代码如下。
          ```html
          <canvas id="myCanvas" width=500" height="500"></canvas>
          <script>
            var canvas=document.getElementById('myCanvas')
            var ctx= canvas.getContext('2d')
            ctx.rect(100,100,300,200)
            ctx.fillStyle = 'pink'
            ctx.fill() 
          </script>
          ```
      17. 本地存储的数据有生命周期吗？
          1.  本地存储的数据没有生命周期，它将一直存储数据，直到用户从浏览器清除或者使用 JavaScript代码移除。
2. CSS3
   1. 选择器 **!important > 行内样式>ID选择器 > 类选择器 > 标签 > 通配符 > 继承 > 浏览器默认属性**
      1. id选择器(#myid)
      2. 类选择器(.myclass)
      3. 属性选择器(a\[rel="external"\])
      4. 伪类选择器(a:hover, li:nth-child)
      5. 标签选择器(div, h1,p)
      6. 相邻选择器（h1 + p）
      7. 子选择器(ul > li)
      8. 后代选择器(li a)
      9. 通配符选择器(\*)
   2. CSS 盒子模型
      1. 标准盒模型： 一个块的总宽度 = width+margin(左右)+padding(左右)+border(左右)
         1. 在标准的盒子模型中，width 指 content 部分的宽度。
      2. 怪异盒模型： 一个块的总宽度 = width+margin（左右）（既 width 已经包含了 padding 和 border 值）
         1. 在 IE 盒子模型中，width 表示 content+padding+border 这三个部分的宽度。
   3. 清除浮动
      1. 添加额外标签
          ```html
            <div class="parent">
                <!-- 添加额外标签并且添加clear属性 -->
                <div style="clear:both"></div>
                <!-- 也可以加一个br标签 -->
            </div>
          ```
      2. 父级添加overflow属性，或者设置高度
      3. 建立伪类选择器清除浮动
          ```css
            <!-- 在css中添加:after伪元素 -->
            .parent:after{
                /* 设置添加子元素的内容是空 */
                content: '';
                /* 设置添加子元素为块级元素 */
                display: block;
                /* 设置添加的子元素的高度0 */
                height: 0;
                /* 设置添加子元素看不见 */
                visibility: hidden;
                /* 设置clear：both */
                clear: both;
            }
          ```
3. JS
   1. 数组的forEach和map方法有哪些区别？
      1. forEach是对数组的每一个元素执行一次给定的函数。
      2. map是创建一个新数组,该新数组由原数组的每个元素都调用一次提供的函数返回的值。
   2. 常用哪些方法去对数组进行增、删、改
      1. pop():删除数组后面的最后一个元素,返回值为被删除的那个元素。
      2. push():将一个元素或多个元素添加到数组末尾，并返回新的长度。
      3. shift():删除数组中的第一个元素，并返回被删除元素的值。
      4. unshift():将一个或多个元素添加到数组的开头，并返回该数组的新长度。
      5. splice():通过删除或替换现有元素或者原地添加新的元素来修改数组，并以数组形式返回被修改的内容。
      6. reverse(): 反转数组。








## [六合数字](https://www.zhipin.com/job_detail/76df94905a4ef5221XF_0929EVRQ.html) / 面试 / 20230309

**工作职责:**

1. 参与公司产品的开发工作；
2. 参与公司产品的前端的架构与设计；
3. 解决产品开发过程中的技术难题，优化代码提升性能；
4. 负责公司目前平台的前端迭代。
5. 熟悉后端与数据库

**任职要求:**

1. 精通vue技术栈，践行[组件化开发模式](https://www.jianshu.com/p/8cd4981add3f)，熟悉后端；
2. 熟悉[vue常用的技术栈](https://zhuanlan.zhihu.com/p/31161485/)，具备脚手架裁剪，定制改造的能力，[了解uniapp](https://uniapp.dcloud.net.cn/)；具备接口开发能力。
3. [熟悉http](https://juejin.cn/post/7016593221815910408#heading-20)/[xml](https://blog.csdn.net/m0_53917137/article/details/116536895)/jon/webervice等网络通信技术，了解go语言后端原理；
4. 熟悉Nginx容器，掌握自动化构建，发布工具优先，了解MongoDB；
5. 有互联网数藏平台或数字经济相关开发经验优先；
6. 工作积极主动，具有强烈的责任心，事业心，具有良好的沟通，协作能力。











































7. Vue2
   1. 生命周期
8. Vue3
   1. 
9. uniapp
10. canvas
11. svg
12. WebSocket 

### 简历中涉及的部分

项目部分
- 具体负责的内容
- 项目中遇到的问题及解决方案










1. 跨域
2. mvvm && mvp
3. 作用域
4. vuex
5. vue-cli
6. vue-router
7. npm --save









## [TypeScript](https://m.runoob.com/typescript/ts-basic-syntax.html)

TypeScript 是 JavaScript 的超集，扩展了 JavaScript 的语法，因此现有的 JavaScript 代码可与 TypeScript 一起工作无需任何修改，TypeScript 通过类型注解提供编译时的静态类型检查。

TypeScript 可处理已有的 JavaScript 代码，并只对其中的 TypeScript 代码进行编译。

TypeScript是微软开发的一个开源的编程语言，通过在JavaScript的基础上添加静态类型定义构建而成。TypeScript通过TypeScript编译器或Babel转译为JavaScript代码，可运行在任何浏览器，任何操作系统。








## [Gulp, Webpack](https://blog.csdn.net/vergil_/article/details/120481498)

*   正如官网所说 **gulp将开发流程中让人痛苦或耗时的任务自动化，从而减少你所浪费的时间、创造更大价值**
*   `gulp`注重前端开发流程，`gulp`可以进行`js`，`html`，`css`，`img`的压缩打包，是自动化构建工具，可以将多个`js`文件或是`css`压缩成一个文件，并且可以压缩为一行，以此来减少文件体积，加快请求速度和减少请求次数。
*   不仅能对网站资源进行优化，而且在开发过程中很多重复的任务能够使用正确的工具自动完成，让我们可以专注于代码，提高工作效率，简单来说就是配置需要的插件，就能帮你把以前需要手动去做的事情给做了。


*   正如官网所说**本质上，webpack 是一个用于现代 JavaScript 应用程序的 静态模块打包工具**
*   `webpack`侧重模块化打包，`webpack`只认识`javascript`，所以会把所运用的所有资源包括图片、`js`文件、`css`文件等通过`loader`和`plugin`进行处理转化成模块。



## [Sass/Less/Stylus](https://www.jianshu.com/p/faf59287ef37)


这三种都没有阉割css的基本语法，也就是说，即使在项目中使用这三种预处理器的任意一种，也完全可以正常书写css，
一个需要注意的地方是，Stylus可以省略花括号和分号。
重点是分析一下这三款预处理器语言的一些相同的特性：

**sass**
Sass声明变量必须是“$”开头，后面紧跟变量名和变量值，而且变量名和变量值需要使用冒号（：）分隔开。就像CSS属性设置一样：

```php
/*声明变量*/
$mainColor: #963;
/*调用变量*/
body {
 color: $mainColor;
}

```

**less**
LESS样式中声明变量和调用变量和Sass一样，唯一的区别就是变量名前面使用的是“@”字符

**stylus**
在stylus可以以$开头，也可以不用任何符号，注意不要用@，另外调用方法也和less、sass是完全相同的














## [ECharts](https://echarts.apache.org/handbook/zh/get-started/)

*ECharts*是一款基于JavaScript的数据可视化图表库，提供直观，生动，可交互，可个性化定制的数据可视化图表。*ECharts*最初由百度团队开源，并于2018年初捐赠给Apache基金会，成为ASF孵化级项目。





## [Koa.js](http://www.vue5.com/koajs/koajs.html)





## [Node.js 框架对比之 Express VS Koa](https://zhuanlan.zhihu.com/p/32049820)

两者创建一个基础的 Web 服务都非常简单，写法也基本相同，最大的区别是路由处理 Express 是自身集成的，而 Koa 需要引入中间件。






























## uView UI

## Flutter









## 真实面试题

1. 如果线上出现bug，你的git操作流程是什么？
2. [js为什么要延迟加载，有哪些方法可以实现延迟加载](https://www.cnblogs.com/yaya-003/p/12708726.html?ivk_sa=1024320u)
   1. setTimeout
      ```html
      <script type="text/javascript">
        function A(){
          $.post("/lord/login",{name:username,pwd:password},function(){
            alert("Hello World!");
          })
        }
        $(function (){
          setTimeout("A()",1000); //延迟1秒
        })
      </script>
      ```
   2. 动态创建script DOM方式
      ```js
      var element = document.createElement("script");
      element.src = "defer.js";
      document.body.appendChild(element);  
      ```
   3. 使用jquery的getScript方法
      ```js
      //加载并执行 test.js：
      $.getScript("test.js");
      //加载并执行 test.js ，成功后显示信息
      $.getScript("test.js", function(){
        alert("Script loaded and executed.");
      });
      ```
    4. 让js最后加载
       1. **将脚本元素放在文档体的底端（`</body>`标签前面）**，这样脚本就可以在HTML解析完毕后加载了。但此方案的问题是，只有在所有HTML DOM加载完成后才开始脚本的加载/解析过程。对于有大量js代码的大型网站，可能会带来显著的性能损耗。
3. [介绍几个Vue3.0/React16的新特性](https://zhuanlan.zhihu.com/p/92143274)
4. [写一个冒泡排序 function sort(arr) {}](https://blog.csdn.net/weixin_41848005/article/details/120977663)
5. [类组件(class component) 和函数组件(Function component) 之间有何不同?](https://blog.csdn.net/weixin_44730897/article/details/124174192)
6. [什么事高阶组件](https://blog.csdn.net/mapbar_front/article/details/79697863)
7. [React中key的作用](http://www.xiaoshuaipeng.com/interview/React/key.html)
   1. 跟`Vue`一样，`React` 也存在 `Diff`算法，而元素`key`属性的作用是用于判断元素是新创建的还是被移动的元素，从而减少不必要的元素渲染