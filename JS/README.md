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
   1. 作用域
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
      1. 延长局部变量的生命周期
   5. 缺点
      1. 会导致函数变量一直保存在内存中，过多的闭包可能会导致内存泄漏

5. this
   1. 作为普通函数时候 this 指向 window
   2. 当函数被作为对象调用时，this指向该函数
   3. 构造器调用，this指向返回的这个对象
   4. 箭头函数 箭头函数的this绑定看的是this所在函数定义在哪个对象下，就绑定哪个对象。如果有嵌套的情况，则this绑定到最近的一层对象上。 - this的指向就是上下文里对象this指向，偶尔没有上下文对象，this就指向window
   5. 基于Function.prototype上的 **apply、call 和 bind** 调用模式，这三个方法都可以显示的指定调用函数的 this 指向。apply接收参数的是数组，call接受参数列表，bind方法通过传入一个对象，返回一个 this 绑定了传入对象的新函数。这个函数的 this指向除了使用new 时会被改变，其他情况下都不会改变。若为空默认是指向全局对象window。

6. 原型和原型链
7. [节流防抖](https://zhuanlan.zhihu.com/p/466102509)原理、区别以及应用
   1. 作用：节流和防抖作为页面性能优化的一种策略，可以降低回调函数的执行频率，节省计算资源，能有效减少浏览器引擎的损耗，防止出现页面堵塞卡顿现象。
   2. 节流 (简单地说，就是限制一个动作在一段时间内只能执行一次，最先触发的那一次) - 王者荣耀发大招
      1. 概念
         1. 在给定时间内，只能触发一次函数。如果在给定时间内触发多次函数，只有一次生效。
      2. 节流场景
         <!-- 1. scroll 事件，滚动加载更多
         2. input 框实时搜索并发送请求展示搜索联想下拉列表，每隔一秒发送一次请求
         3. 高频点击
         4. 表单重复提交 -->
         5. 鼠标连续不断地触发某事件（如点击事件），单位时间内只触发一次；
         6. 监听滚动事件，例如：懒加载；
         7. 每隔多少秒计算一次相关数据。 
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
   3. 防抖 (简单地说，就是 当一个动作连续触发，只执行最后一次) - 王者荣耀回城
      1. 概念
         1. 在事件被触发n秒后再执行回调，如果在这n秒内又被触发，则重新计时。
      2. 防抖场景
         <!-- 1. window触发resize的时候，不断的调整浏览器窗口大小会不断的触发这个事件，用防抖来让其只触发一次 -->
         1. 登录、短信验证等按钮避免用户点击太快，发行多次请求
         2. 调整浏览器窗口大小时，resize 次数过于频繁，计算过多，造成页面卡顿的情况；
         3. 文本编辑器实时保存；
         4. 搜索框等。














补充：
es6
   set map方法

疑难：
箭头函数this
apply、call 和 bind