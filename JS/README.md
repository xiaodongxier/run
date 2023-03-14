1. 基本的数据类型
   1. 基本类型（值类型）
      1. string，number，boolean，undefined，null，symbol
   2. 引用类型（复杂数据类型）
      1. Object
      2. Function
      3. Array
      4. Date
      5. ...
2. JS中的数据类型检测方案
   1. typeof
      ```js
        console.log('undefined', typeof undefined )      // undefined
        console.log('null', typeof null )      // object
        console.log('true', typeof true )      // boolean
        console.log('[]', typeof [] )      // object
        console.log('{}', typeof {} )      // object
        console.log('String', typeof String )      // function
        console.log('Boolean', typeof Boolean )      // function
        console.log('Number', typeof Number )      // function
        console.log('Symbol', typeof Symbol )      // function
        console.log('Function', typeof Function )      // function
        console.log('Symbol()', typeof Symbol() )      // Symbol
        console.log('console.log()', typeof console.log() )      // undefined
      ```
      1. 快速区分基本数据类型
      2. 不能将Object，Array和Null区分，都返回Object
    2. instanceof
      ```js
        console.log( 1 instanceof Number )       // false
        console.log( '1' instanceof String )       // false
        console.log( true instanceof Boolean )       // false
        console.log( [] instanceof Array )        // true
        console.log( [] instanceof Object )        // true
        console.log( {} instanceof Object )        // true
        console.log( Function instanceof Object )        // true
        console.log( Function instanceof Function )        // true
      ```
      1. 能区分object，function，array适合用于判断自定义的类实例对象
      2. Number，String，Boolean基本数据无法判断
    3. Object.prototype.toString.call()
      ```js
        var toString = Object.prototype.toString;
        console.log(toString.call(1))   //[object Number]
        console.log(toString.call('1'))   //[object String]
        console.log(toString.call(true))   //[object Boolean]
        console.log(toString.call(undefined))   //[object Undefined]
        console.log(toString.call(null))   //[object Null]
        console.log(toString.call(Symbol))   //[object Function]
        console.log(toString.call(Symbol()))   //[object Symbol]
        console.log(toString.call([]))   //[object Array]
        console.log(toString.call({}))   //[object Object]
      ```
      1. 能精准判断数据类型
      2. 写法太长不容易记忆，推荐封装后使用

2. var/let/const
   1. var全局变量
      1. 存在变量提升，可以先使用后声明；
      2. 相同作用域内可以重复声明使用
   2. let块级变量
      1. 只能在作用域里面访问，必须先声明后使用；
      2. 不能重复声明
   3. const常量
      1. 只能作用域里访问，必须先声明且必须赋值
      2. 不能修改
      3. 不能重复声明

3. 作用域和作用域链
   1. 作用域 （作用域指一个变量的作用的范围。）
      1. 定义：简单来说作用域就是变量与函数的可访问范围，由当前环境与上层环境的一系列变量对象组成
      2. 作用：作用域最大的用处就是**隔离变量**，不同作用域下同名变量不会有冲突。
      3. 全局作用域：代码在程序的任何地方都能被访问，window 对象的内置属性都拥有全局作用域。
      4. 函数作用域：在固定的代码片段才能被访问
   2. 作用域链
      1. 变量到 创建该变量 的函数的作用域中取值。但是如果在当前作用域中没有查到，就会向上级作用域去查，直到查到全局作用域，这么一个查找过程形成的链条就叫做作用域链。

4. 闭包及作用
   1. 闭包
      1. 能够读取其他函数内的变量的函数
   2. 作用
      1. 模仿块级作用域
      2. 保护外部函数的变量 能够访问函数定义时所在的词法作用域(阻止其被回收)
      3. 封装私有化变量
      4. 创建模块
   3. 形成条件
      1. 函数的嵌套
      2. 内部函数引用外部函数的局部变量，延长外部函数的生命周期
   4. 优点
      1. 变量长期驻扎在内存中,可以重复使用变量
      2. 避免全局变量的污染
      3. 
   5. 缺点
      1. 常驻内存 增大内存的使用量 使用不当会造成内存泄漏
         1. 在退出函数之前，将不使用的局部变量全部删除。
      2. 会导致函数变量一直保存在内存中，过多的闭包可能会导致内存泄漏

5. this
   1. 作为普通函数时候 this 指向 window
   2. 当函数被作为对象调用时，this指向该函数
   3. 构造器调用，this指向返回的这个对象
   4. 箭头函数 箭头函数的this绑定看的是this所在函数定义在哪个对象下，就绑定哪个对象。如果有嵌套的情况，则this绑定到最近的一层对象上。 - this的指向就是上下文里对象this指向，偶尔没有上下文对象，this就指向window
   5. 基于Function.prototype上的 **apply、call 和 bind** 调用模式，这三个方法都可以显示的指定调用函数的 this 指向。apply接收参数的是数组，call接受参数列表，bind方法通过传入一个对象，返回一个 this 绑定了传入对象的新函数。这个函数的 this指向除了使用new 时会被改变，其他情况下都不会改变。若为空默认是指向全局对象window。

6. 原型和原型链
7. [节流防抖](https://zhuanlan.zhihu.com/p/466102509)原理、区别以及应用 - [demo](https://gitcdn.xiaodongxier.com/pages/20230314205738.html)
   1. 作用：节流和防抖作为页面性能优化的一种策略，可以降低回调函数的执行频率，节省计算资源，能有效减少浏览器引擎的损耗，防止出现页面堵塞卡顿现象。
   2. 节流 - 控制执行次数/控制高频事件执行次数 (简单地说，就是限制一个动作在一段时间内只能执行一次，最先触发的那一次) - 王者荣耀发大招
      1. 概念
         1. 在给定时间内，只能触发一次函数。如果在给定时间内触发多次函数，只有一次生效。
      2. 节流场景
         1. 鼠标连续不断地触发某事件（如点击事件），单位时间内只触发一次；
         2. 监听滚动事件，例如：懒加载；
         3. 滚动加载，加载更多或滚到底部监听
         4. 搜索框，搜索联想功能
      3. 代码实现
         ```js
         function throttle (fn,delay){
            let timer = null
            return ()=>{
               if (timer){return}
               timer = setTimeout(() => {
                     fn.apply(this,arguments)
                     timer = null
               }, delay);       
            }
         } 
         ```
   3. 防抖 - 只执行最后一次/用户触发过于频繁只要最后一次 (简单地说，就是 当一个动作连续触发，只执行最后一次) - 王者荣耀回城
      1. 概念
         1. 在事件被触发n秒后再执行回调，如果在这n秒内又被触发，则重新计时。
      2. 防抖场景
         <!-- 1. window触发resize的时候，不断的调整浏览器窗口大小会不断的触发这个事件，用防抖来让其只触发一次 -->
         1. 登录、短信验证等按钮避免用户点击太快，发行多次请求
         2. 调整浏览器窗口大小时，resize 次数过于频繁，计算过多，造成页面卡顿的情况；
         3. 文本编辑器实时保存；
         4. 搜索框搜索输入。只需用户最后一次输入完，再发送请求
         5. 手机号、邮箱验证输入检测
      3. 代码操作
         ```html
           <input type="text">
           <script>
            // 最后一条为什么不会被清掉呢
            // 因为0.5秒内没有input事件，没有触发函数
            let inp = document.querySelector('input');
            let time = null
            inp.oninput = function () {
               if (time !== null) {
                  clearTimeout(time)
               }
               time = setTimeout(() => {
                  console.log(this.value)
               }, 500)
            }
            </script>
         ```
   4. 节流是多次操作变成少量操作，防抖是只要最后一次操作
   5. 例如，都设置时间频率为500ms，在2秒时间内，频繁触发函数，节流，每隔 500ms 就执行一次。防抖，则不管调动多少次方法，在2s后，只会执行一次
      ![节流防抖](https://gitcdn.xiaodongxier.com/image/20230314215510.jpg)
8. Git
   1. 查看分支：git branch
   2. 创建分支：git branch 分支name
   3. 切换分支：git checkout
   4. 创建+切换分支：git checkout -b 分支name
   5. 合并某分支到当前分支：git merge
   6. 删除本地分支：git branch -d 分支name
   7. 删除远程分支：git push origin --delete 分支name

9. Babel
   1.  Babel 是一个 JavaScript 编译器，是一个工具链，主要用于将采用 ECMAScript 2015+ 语法编写的代码转换为向后兼容的 JavaScript 语法，以便能够运行在当前和旧版本的浏览器或其他环境中。
   2.  Babel 的功能很纯粹，它只是一个编译器。大多数编译器的工作过程可以分为三部分：
       1.  解析（Parse） ：将源代码转换成更加抽象的表示方法（例如抽象语法树）。包括词法分析和语法分析。词法分析主要把字符流源代码（Char Stream）转换成令牌流（ Token Stream），语法分析主要是将令牌流转换成抽象语法树（Abstract Syntax Tree，AST）。
       2.  转换（Transform） ：通过 Babel 的插件能力，对（抽象语法树）做一些特殊处理，将高版本语法的 AST 转换成支持低版本语法的 AST。让它符合编译器的期望，当然在此过程中也可以对 AST 的 Node 节点进行优化操作，比如添加、更新以及移除节点等。
       3.  生成（Generate） ：将 AST 转换成字符串形式的低版本代码，同时也能创建 Source Map 映射。

10. webpack 做过哪些优化，开发效率方面、打包策略方面等等
    1.  q


11. 项目优化
   1. 减少请求数
       1. JS、CSS打包到HTML。JS控制图片异步加载、懒加载。小型图片使用data-url。
   2.  较少传输体积
       1.  尽量使用SVG\gradient代替图片。根据机型和网络状况控制图片清晰度。对低清晰度图片使用锐化来提升体验。设计上避免大型背景图。
   3. 使用CDN加速
      1. 内容分发网络，是建立再承载网基础上的虚拟分布式网络，能够将源站内容缓存到全国或全球的节点服务器上。用户就近获取内容，提高了资源的访问速度，分担源站压力。
   4. 第三方库的按需加载
   5. 移除生产环境的控制台打印
   6. 性能问题
      1. 页面加载性能
      2. 动画性能
      3. 操作性能












**补充：**
es6
   set map方法

**疑难：**
箭头函数this
apply、call 和 bind
webpack 做过哪些优化，开发效率方面、打包策略方面等等
