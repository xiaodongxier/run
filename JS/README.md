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
