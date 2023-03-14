1. 双向数据绑定的原理
2. MVVM、MVC、MVP的区别
   1. mvvm：
      1. m是model层，代表数据模型，负责数据和业务逻辑
      2. v是view层，视图层，负责数据的展示
      3. vm是监听m层的数据变化并控制v层视图的更新，处理用户的交互操作
   2. mvc
      1. m是model层，页面的业务数据，数据的交互操作 - 观察者模式，发生变化回通知v更新
      2. v是view层，负责页面的显示逻辑 - 观察者模式 （1,2过于复杂的会出现耦合）
      3. c是control层，控制器 - m与v的纽带，负责处理用户与应用的操作，当用户与页面产生交互的时候，c中的事件触发器开始工作，通过调用m层，完成对m的修改，然后通知v层进行更新
   3. mvp
      1. v和m类似于mvc中的
      2. p ：使用 Presenter 来实现对 View 层和 Model 层的解耦。View 层的接口暴露给了 Presenter 因此可以在 Presenter 中将 Model 的变化和 View 的变化绑定在一起，以此来实现 View 和 Model 的同步更新。这样就实现了对 View 和 Model 的解耦，Presenter 还包含了其他的响应逻辑。
      3. 由于View层和Model层都需要经过Presenter层，导致Presenter层比较复杂，维护起来也会有一定的问题；而且，因为没有绑定数据，所有数据都需要Presenter层进行“手动同步”，代码量较大，虽然比起MVC框架好很多，但还是有比较多冗余部分。
3. 说说mvvm和他的优点
   1. 视图模型双向绑定，是Model-View-ViewModel的缩写，也就是把MVC中的Controller演变成ViewModel。Model层代表数据模型，View代表UI组件，ViewModel是View和Model层的桥梁，数据会绑定到viewModel层并自动将数据渲染到页面中，视图变化的时候会通知viewModel层更新数据。以前是操作DOM结构更新视图，现在是数据驱动视图。
   2. 优点
      1. 低耦合
      2. 可重用性
      3. 独立开发
      4. 可测试

4. Computed 和 Watch 的区别
   1. computed 
5. Computed 和 methods 的区别
6. slot是什么？作用？原理
7. 过滤器的作用，如何实现一个过滤器
8. 常见的事件修饰符及其作用
9.  v-if、v-show、v-html 的原理
10. v-if和v-show的区别
11. v-model 是如何实现的，语法糖实际是什么？
12. data为什么是一个函数而不是对象
13. 对keep-alive的理解，它是如何实现的，具体缓存的是什么？
14. Vue中封装的数组方法有哪些，其如何实现页面更新
15. Vue 单页应用与多页应用的区别 
