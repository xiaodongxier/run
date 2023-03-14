# JS


## 作用域


## 闭包


## 跨域













## JS中的8种数据类型及区别

包括值类型(基本对象类型)和引用类型(复杂对象类型)

**基本类型(值类型)：** Number(数字),String(字符串),Boolean(布尔),Symbol(符号),null(空),undefined(未定义)在内存中占据固定大小，保存在栈内存中

**引用类型(复杂数据类型)：** Object(对象)、Function(函数)。其他还有Array(数组)、Date(日期)、RegExp(正则表达式)、特殊的基本包装类型(String、Number、Boolean) 以及单体内置对象(Global、Math)等 引用类型的值是对象 保存在堆内存中，栈内存存储的是对象的变量标识符以及对象在堆内存中的存储地址。




## JS中的数据类型检测方案

### 1.typeof

```js
console.log(typeof 1);               // number
console.log(typeof true);            // boolean
console.log(typeof 'mc');            // string
console.log(typeof Symbol)           // function
console.log(typeof Symbol());        // symbol
console.log(typeof function(){});    // function
console.log(typeof console.log());   // undefined
console.log(typeof []);              // object
console.log(typeof {});              // object
console.log(typeof null);            // object
console.log(typeof undefined);       // undefined
复制代码
```

优点：能够快速区分基本数据类型

缺点：不能将Object、Array和Null区分，都返回object

### 2.instanceof

```js
console.log(1 instanceof Number);                    // false
console.log(true instanceof Boolean);                // false
console.log('str' instanceof String);                // false
console.log([] instanceof Array);                    // true
console.log(function(){} instanceof Function);       // true
console.log({} instanceof Object);                   // true
```

优点：能够区分Array、Object和Function，适合用于判断自定义的类实例对象

缺点：Number，Boolean，String基本数据类型不能判断

### 3.Object.prototype.toString.call()

```js
var toString = Object.prototype.toString;
console.log(toString.call(1));                      //[object Number]
console.log(toString.call(true));                   //[object Boolean]
console.log(toString.call('mc'));                   //[object String]
console.log(toString.call([]));                     //[object Array]
console.log(toString.call({}));                     //[object Object]
console.log(toString.call(function(){}));           //[object Function]
console.log(toString.call(undefined));              //[object Undefined]
console.log(toString.call(null));                   //[object Null]
```

优点：精准判断数据类型

缺点：写法繁琐不容易记，推荐进行封装后使用






## JS 中 this 的五种情况


1.  作为普通函数执行时，`this`指向`window`。
2.  当函数作为对象的方法被调用时，`this`就会指向`该对象`。
3.  构造器调用，`this`指向`返回的这个对象`。
4.  箭头函数 箭头函数的`this`绑定看的是`this所在函数定义在哪个对象下`，就绑定哪个对象。如果有嵌套的情况，则this绑定到最近的一层对象上。
5.  基于Function.prototype上的 `apply 、 call 和 bind` 调用模式，这三个方法都可以显示的指定调用函数的 this 指向。`apply`接收参数的是数组，`call`接受参数列表，` bind`方法通过传入一个对象，返回一个` this `绑定了传入对象的新函数。这个函数的` this`指向除了使用`new \`时会被改变，其他情况下都不会改变。若为空默认是指向全局对象window。



## [箭头函数和普通函数有什么区别](https://juejin.cn/post/7204707115062411320?)

1. 箭头函数不会创建自身的this，只会从上一级继承this，箭头函数的this在定义的时候就已经确认了，之后不会改变。同时箭头函数无法作为构造函数使用，没有自身的prototype，也没有arguments。






## 作用域和作用域链



创建函数的时候，已经声明了当前函数的作用域==>`当前创建函数所处的上下文`。如果是在全局下创建的函数就是`[[scope]]:EC(G)`，函数执行的时候，形成一个全新的私有上下文`EC(FN)`，供字符串代码执行(进栈执行)

定义：简单来说作用域就是变量与函数的可访问范围，`由当前环境与上层环境的一系列变量对象组成`
1.全局作用域：代码在程序的任何地方都能被访问，window 对象的内置属性都拥有全局作用域。
2.函数作用域：在固定的代码片段才能被访问

作用：作用域最大的用处就是`隔离变量`，不同作用域下同名变量不会有冲突。

**作用域链参考链接**一般情况下，变量到 创建该变量 的函数的作用域中取值。但是如果在当前作用域中没有查到，就会向上级作用域去查，直到查到全局作用域，这么一个查找过程形成的链条就叫做作用域链。






## 闭包的两大作用：保存/保护


**闭包的概念**

函数执行时形成的私有上下文EC(FN)，正常情况下，代码执行完会出栈后释放;但是特殊情况下，如果当前私有上下文中的某个东西被上下文以外的事物占用了，则上下文不会出栈释放，从而形成不销毁的上下文。 函数执行函数执行过程中，会形成一个全新的私有上下文，可能会被释放，可能不会被释放，不论释放与否，他的作用是：

（1）保护：划分一个独立的代码执行区域，在这个区域中有自己私有变量存储的空间，保护自己的私有变量不受外界干扰（操作自己的私有变量和外界没有关系）；

（2）保存：如果当前上下文不被释放【只要上下文中的某个东西被外部占用即可】，则存储的这些私有变量也不会被释放，可以供其下级上下文中调取使用，相当于把一些值保存起来了；

我们把函数执行形成私有上下文，来保护和保存私有变量机制称为`闭包`。

> 闭包是指有权访问另一个函数作用域中的变量的函数--《JavaScript高级程序设计》

**稍全面的回答**： 在js中变量的作用域属于函数作用域, 在函数执行完后,作用域就会被清理,内存也会随之被回收,但是由于闭包函数是建立在函数内部的子函数, 由于其可访问上级作用域,即使上级函数执行完, 作用域也不会随之销毁, 这时的子函数(也就是闭包),便拥有了访问上级作用域中变量的权限,即使上级函数执行完后作用域内的值也不会被销毁。

**闭包的特性**：

*   1、内部函数可以访问定义他们外部函数的参数和变量。(作用域链的向上查找，把外围的作用域中的变量值存储在内存中而不是在函数调用完毕后销毁)设计私有的方法和变量，避免全局变量的污染。

  1.1.闭包是密闭的容器，，类似于set、map容器，存储数据的

  1.2.闭包是一个对象，存放数据的格式为 key-value 形式

*   2、函数嵌套函数

*   3、本质是将函数内部和外部连接起来。优点是可以读取函数内部的变量，让这些变量的值始终保存在内存中，不会在函数被调用之后自动清除

**闭包形成的条件**：

1.  函数的嵌套
2.  内部函数引用外部函数的局部变量，延长外部函数的变量生命周期
**闭包的用途**：

1.  模仿块级作用域
2.  保护外部函数的变量 能够访问函数定义时所在的词法作用域(阻止其被回收)
3.  封装私有化变量
4.  创建模块
**闭包应用场景**

闭包的两个场景，闭包的两大作用：`保存/保护`。 在开发中, 其实我们随处可见闭包的身影, 大部分前端JavaScript 代码都是“事件驱动”的,即一个事件绑定的回调方法; 发送ajax请求成功|失败的回调;setTimeout的延时回调;或者一个函数内部返回另一个匿名函数,这些都是闭包的应用。

**闭包的优点**：延长局部变量的生命周期

**闭包缺点**：会导致函数的变量一直保存在内存中，过多的闭包可能会导致内存泄漏





## 简述MVVM


**什么是MVVM？**

`视图模型双向绑定`，是`Model-View-ViewModel`的缩写，也就是把`MVC`中的`Controller`演变成`ViewModel。Model`层代表数据模型，`View`代表UI组件，`ViewModel`是`View`和`Model`层的桥梁，数据会绑定到`viewModel`层并自动将数据渲染到页面中，视图变化的时候会通知`viewModel`层更新数据。以前是操作DOM结构更新视图，现在是`数据驱动视图`。

**MVVM的优点：**

1.`低耦合`。视图（View）可以独立于Model变化和修改，一个Model可以绑定到不同的View上，当View变化的时候Model可以不变化，当Model变化的时候View也可以不变；
2.`可重用性`。你可以把一些视图逻辑放在一个Model里面，让很多View重用这段视图逻辑。
3.`独立开发`。开发人员可以专注于业务逻辑和数据的开发(ViewModel)，设计人员可以专注于页面设计。
4.`可测试`。





## Vue底层实现原理


vue.js是采用数据劫持结合发布者-订阅者模式的方式，通过Object.defineProperty()来劫持各个属性的setter和getter，在数据变动时发布消息给订阅者，触发相应的监听回调
Vue是一个典型的MVVM框架，模型（Model）只是普通的javascript对象，修改它则试图（View）会自动更新。这种设计让状态管理变得非常简单而直观

**Observer（数据监听器）** : Observer的核心是通过Object.defineProprtty()来监听数据的变动，这个函数内部可以定义setter和getter，每当数据发生变化，就会触发setter。这时候Observer就要通知订阅者，订阅者就是Watcher

**Watcher（订阅者）** : Watcher订阅者作为Observer和Compile之间通信的桥梁，主要做的事情是：

1.  在自身实例化时往属性订阅器(dep)里面添加自己
2.  自身必须有一个update()方法
3.  待属性变动dep.notice()通知时，能调用自身的update()方法，并触发Compile中绑定的回调

**Compile（指令解析器）** : Compile主要做的事情是解析模板指令，将模板中变量替换成数据，然后初始化渲染页面视图，并将每个指令对应的节点绑定更新函数，添加鉴定数据的订阅者，一旦数据有变动，收到通知，更新试图



## 谈谈对vue生命周期的理解？


每个`Vue`实例在创建时都会经过一系列的初始化过程，`vue`的生命周期钩子，就是说在达到某一阶段或条件时去触发的函数，目的就是为了完成一些动作或者事件

*   `create阶段`：vue实例被创建
    `beforeCreate`: 创建前，此时data和methods中的数据都还没有初始化
    `created`： 创建完毕，data中有值，未挂载
*   `mount阶段`： vue实例被挂载到真实DOM节点
    `beforeMount`：可以发起服务端请求，去数据
    `mounted`: 此时可以操作DOM
*   `update阶段`：当vue实例里面的data数据变化时，触发组件的重新渲染
    `beforeUpdate` :更新前
    `updated`：更新后
*   `destroy阶段`：vue实例被销毁
    `beforeDestroy`：实例被销毁前，此时可以手动销毁一些方法
    `destroyed`:销毁后

### 组件生命周期

生命周期（父子组件） 父组件beforeCreate --> 父组件created --> 父组件beforeMount --> 子组件beforeCreate --> 子组件created --> 子组件beforeMount --> 子组件 mounted --> 父组件mounted -->父组件beforeUpdate -->子组件beforeDestroy--> 子组件destroyed --> 父组件updated

**加载渲染过程** 父beforeCreate->父created->父beforeMount->子beforeCreate->子created->子beforeMount->子mounted->父mounted

**挂载阶段** 父created->子created->子mounted->父mounted

**父组件更新阶段** 父beforeUpdate->父updated

**子组件更新阶段** 父beforeUpdate->子beforeUpdate->子updated->父updated

**销毁阶段** 父beforeDestroy->子beforeDestroy->子destroyed->父destroyed







## `computed与watch`

通俗来讲，既能用 computed 实现又可以用 watch 监听来实现的功能，推荐用 computed， 重点在于 computed 的缓存功能 computed 计算属性是用来声明式的描述一个值依赖了其它的值，当所依赖的值或者变量 改变时，计算属性也会跟着改变； watch 监听的是已经在 data 中定义的变量，当该变量变化时，会触发 watch 中的方法。

**watch 属性监听** 是一个对象，键是需要观察的属性，值是对应回调函数，主要用来监听某些特定数据的变化，从而进行某些具体的业务逻辑操作,监听属性的变化，需要在数据变化时执行异步或开销较大的操作时使用

**computed 计算属性** 属性的结果会被`缓存`，当`computed`中的函数所依赖的属性没有发生改变的时候，那么调用当前函数的时候结果会从缓存中读取。除非依赖的响应式属性变化时才会重新计算，主要当做属性来使用 `computed`中的函数必须用`return`返回最终的结果 `computed`更高效，优先使用。`data 不改变，computed 不更新。`

**使用场景** `computed`：当一个属性受多个属性影响的时候使用，例：购物车商品结算功能 `watch`：当一条数据影响多条数据的时候使用，例：搜索数据



































## 跨域


[跨域资源共享 CORS 详解：https://www.ruanyifeng.com/blog/2016/04/cors.html](https://www.ruanyifeng.com/blog/2016/04/cors.html)

[跨域，不可不知的基础概念：https://juejin.cn/post/7003232769182547998](https://juejin.cn/post/7003232769182547998)

浏览器的同源策略

协议 域名 端口  

**出现原因**：由于同源策略限制，同源策略是浏览器最核心也是最基本的安全功能，Web是构建在同源策略基础之上的。同源策略会阻止一个域的JS脚本和另一个域的内容进行交互。同源（指在同一个域）就是两个页面具有相同的协议(protocol)、主机(host)和端口号(port)。
**什么是跨域**：当一个请求的url的协议、域名、端口三者之间任意一个与当前页面url不同即为跨域
**非同源限制**：
（1）无法读取非同源网页的Cookie、LocalStorage和IndexedDB
（2）无法接触非同源网页的DOM
（3）无法向非同源地址发送AJAX请求
**跨域解决方法**：
（1）设置document.domain解决无法读取非同源的Cookie问题
浏览器通过document.domain属性来检查两个页面是否同源，因此将两个页面设置相同的document.domain，就可以共享Cookie（仅限主域相同，子域不同的跨域应用场景）
（2）跨文档通信API：window.postMessage()
调用postMessage方法实现父窗口 http://test1.com向子窗口http://test2.com发消息（子窗口同样可以使用该方法发送消息给父窗口）
主要使用于以下场景：


### 解决跨域的方法

1. JSONP跨域（缺点：只能发送GET请求）

> JSONP跨域是利⽤`<script>`标签没有跨域限制，通过`<script>`标签的src属性发送带有callback参数的GET请求，服务端将接⼝返回数据拼凑在callback函数中，返回给浏览器，浏览器解析执⾏，从⽽前端拿到callback函数中返回的数据。

> JSONP是服务器与客户端跨源通信的常用方法。最大特点就是简单实用，兼容性好（兼容低版本IE），缺点是只支持get请求，不支持post请求

```js
// 原生实现
<script src="http://test.com/data.php?callback=doSomeThing"></script>
// 向服务器test.com发起请求，该请求的查询字符串有一个callback参数，用来指定回调函数的名字
// 处理服务器返回回调函数的数据
<script tyoe="text/javascript">
  function doSomeThing(res) {
    // 处理获得的数据
    console.log(res.data);
  }
</script>

// jQuery ajax
$.ajax({
  url: 'http://www.test.com:8080/login',
  type: 'get',
  dataType: 'jsonp',  // 请求方式为jsonp
  jsonCallback: 'handleCallback',  // 自定义回调函数名
  data: {}
})

// Vue.js
this.$http.jsonp('http://www.domain2.com:8080/login', {
  params: {},
  jsonp: 'handleCallback',
}).then((res) => {
  console.log(res);
});
```



2. CORS跨域


CORS是跨域资源分享（Cross-Origin Resource Sharing）的缩写。是W3C标准，属于跨源AJAX请求的根本解决方法。
（分为两种方式，是否携带cookie决定）
\-== 普通跨域请求：只需要服务器设置Access-Control-Allow-Origin==
\-== 带cookie跨域请求，前后端都需要进行设置==
**前端设置**，根据 xhr.withCredentials字段判断是否带有cookie


```js
// 原生ajax
var xhr = new XMLHttpRequest();  // IE8/9需要用window.XDomainRequest做兼容

// 假设固定前端携带cookie发起请求
xhr.withCredentials = true;

xhr.open('post', 'http://www.music.com:8080/login', true);
xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlopended');
xhr.send('user=admin');

xhr.onreadystatechange = function() {
  if (xhr.readyState === 4 && xhr.status == 200) {
    alert(xhr.responseText);
  };
};

//  jQuery ajax
$.ajax({
  url: 'http://www.music.com:8080/login',
  type: 'get',
  data: {},
  xhrFields: {
    withCredentials: true  // 前端设置是否带cookie
  },
  crossDomain: true  // 会让请求头中包含跨域的额外信息，但不会含cookie
})

// vue-resource
Vue.http.options.credentials = true;
 
// axios
axios.defaults.withCredentials = true 

```


服务器设置

> 服务器端对于CORS的支持，主要是通过设置Access-Control-Allow-Origin来进行的。如果浏览器检测到相应的设置，就可以允许Ajax进行跨域的访问。

- Java后台设置

```js
// 允许跨域访问的域名，若有端口需要写全（协议+域名+端口），若没有端口末尾不用加'/'
response.setHeader("Access-Control-Allow-Origin", "http://www.music.com");

// 允许前端带认证cookie：启用此项后，上面的域名不能为'*'，必须指定具体的域名，否则浏览器会发出提示
response.setHeader("Access-Control-Allow-Credentials", "true");
// 提示OPTIONS检验时，后端需要设置两个常用的自定义头
response.setHeader("Access-Control-Allow-Headers", "Content-Type, X-Rquested-with");
```

- Node.js后台

```js
var http = request('http');
var serve = http.createServer();
var qs = require('querystring');  // Node.js内置模块querystring

server.on('request', function(req, res) {
  var postData = '';
  
  // 数据块接受中
  req.addLisener('data', function(chunk) {
    postData += chunk;
  })
  
  // 数据接收完毕
  req.addListener('end', function() {
    postData = qs.parse(postData);  // 将postData转为对象
    // querystring.parse()方法返回的对象不是原型，会继承自JavaScript的Object。意味着典型的Object方法如obj.toString()、obj.hasOwnProperty()等没有被定义并且不起作用。解决方法是：先将对象进行JSON字符串转化(JSON.stringify())，然后再转化成对象(JSON.parse())
    
    // 数据后台设置
    res.writeHead(200, {
      'Access-Control-Allow-Credentials': 'true',  // 后端允许发送Cookie
      'Access-Control-Allow-Origin': 'http://www.music.com',  // 允许访问的域（协议+域名+端口）
      'Set-Cookie': 'l=a123456;Path=/;Music=www.music.com;HttpOnly'  // HttpOnly属性，无法通过js脚本获取cookie信息，XSS攻击中无法通过document对象直接获取cookie
    })；

    res.write(JSON.stringify(postData));
    res.end();
  });
});

server.listen('8080');
console.log('Server is runing!');
```

- PHP后台(网上寻找)

```js
<?php
header("Access-Control-Allow-Origin: *");
```






## Cookie、sessionStorage、localStorage 的区别

**相同点**：

*   存储在客户端

**不同点**：

*   cookie数据大小不能超过4k；sessionStorage和localStorage的存储比cookie大得多，可以达到5M+
*   cookie设置的过期时间之前一直有效；localStorage永久存储，浏览器关闭后数据不丢失除非主动删除数据；sessionStorage数据在当前浏览器窗口关闭后自动删除
*   cookie的数据会自动的传递到服务器；sessionStorage和localStorage数据保存在本地

































## 作用域




## 原型链



## 闭包
























































