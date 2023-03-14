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

