# CSS


## CSS 选择器及优先级

**选择器**

*   id选择器(#myid)
*   类选择器(.myclass)
*   属性选择器(a\[rel="external"\])
*   伪类选择器(a:hover, li:nth-child)
*   标签选择器(div, h1,p)
*   相邻选择器（h1 + p）
*   子选择器(ul > li)
*   后代选择器(li a)
*   通配符选择器(\*)

**优先级：**

*   `!important`
*   内联样式（1000）
*   ID选择器（0100）
*   类选择器/属性选择器/伪类选择器（0010）
*   元素选择器/伪元素选择器（0001）
*   关系选择器/通配符选择器（0000）

带!important 标记的样式属性优先级最高； 样式表的来源相同时：`!important > 行内样式>ID选择器 > 类选择器 > 标签 > 通配符 > 继承 > 浏览器默认属性`



## position 属性的值有哪些及其区别

**固定定位 fixed**： 元素的位置相对于浏览器窗口是固定位置，即使窗口是滚动的它也不会移动。Fixed 定 位使元素的位置与文档流无关，因此不占据空间。 Fixed 定位的元素和其他元素重叠。

**相对定位 relative**： 如果对一个元素进行相对定位，它将出现在它所在的位置上。然后，可以通过设置垂直 或水平位置，让这个元素“相对于”它的起点进行移动。 在使用相对定位时，无论是 否进行移动，元素仍然占据原来的空间。因此，移动元素会导致它覆盖其它框。

**绝对定位 absolute**： 绝对定位的元素的位置相对于最近的已定位父元素，如果元素没有已定位的父元素，那 么它的位置相对于。absolute 定位使元素的位置与文档流无关，因此不占据空间。 absolute 定位的元素和其他元素重叠。

**粘性定位 sticky**： 元素先按照普通文档流定位，然后相对于该元素在流中的 flow root（BFC）和 containing block（最近的块级祖先元素）定位。而后，元素定位表现为在跨越特定阈值前为相对定 位，之后为固定定位。

**默认定位 Static**： 默认值。没有定位，元素出现在正常的流中（忽略 top, bottom, left, right 或者 z-index 声 明）。 inherit: 规定应该从父元素继承 position 属性的值。

**inherit**： 规定应该从父元素继承 position 属性的值。(IE8以及往前的版本都不支持inherit属性。)



## BFC（块级格式上下文）

**BFC的概念**

`BFC` 是 `Block Formatting Context` 的缩写，即块级格式化上下文。`BFC`是CSS布局的一个概念，是一个独立的渲染区域，规定了内部box如何布局， 并且这个区域的子元素不会影响到外面的元素，其中比较重要的布局规则有内部 box 垂直放置，计算 BFC 的高度的时候，浮动元素也参与计算。

**BFC的原理布局规则**

*   内部的Box会在`垂直方向`，一个接一个地放置
*   Box`垂直方向的距离由margin决定`。属于同一个BFC的两个相邻Box的margin会发生重叠
*   每个元素的margin box的左边， 与包含块border box的左边相接触(对于从左往右的格式化，否则相反
*   BFC的区域`不会与float box重叠`
*   BFC是一个独立容器，容器里面的`子元素不会影响到外面的元素`
*   计算BFC的高度时，`浮动元素也参与计算高度`
*   元素的类型和`display属性，决定了这个Box的类型`。不同类型的Box会参与不同的`Formatting Context`。

**如何创建BFC？**

*   根元素，即HTML元素
*   float的值不为none
*   position为absolute或fixed
*   display的值为inline-block、table-cell、table-caption
*   overflow的值不为visible

**BFC的使用场景**

*   去除边距重叠现象
*   清除浮动（让父元素的高度包含子浮动元素）
*   避免某元素被浮动元素覆盖
*   避免多列布局由于宽度计算四舍五入而自动换行






## 让一个元素水平垂直居中

**水平居中**

*   对于 行内元素 : `text-align: center`;

*   对于确定宽度的块级元素：

（1）width和margin实现。`margin: 0 auto`;

（2）绝对定位和margin-left: (父width - 子width）/2, 前提是父元素position: relative

*   对于宽度未知的块级元素

（1）`table标签配合margin左右auto实现水平居中`。使用table标签（或直接将块级元素设值为 display:table），再通过给该标签添加左右margin为auto。

（2）inline-block实现水平居中方法。display：inline-block和text-align:center实现水平居中。

（3）`绝对定位+transform`，translateX可以移动本身元素的50%。

（4）flex布局使用`justify-content:center`

**垂直居中**

1.  利用 `line-height` 实现居中，这种方法适合纯文字类
2.  通过设置父容器 相对定位 ，子级设置 `绝对定位`，标签通过margin实现自适应居中
3.  弹性布局 flex :父级设置display: flex; 子级设置margin为auto实现自适应居中
4.  父级设置相对定位，子级设置绝对定位，并且通过位移 transform 实现
5.  `table 布局`，父级通过转换成表格形式，`然后子级设置 vertical-align 实现`。（需要注意的是：vertical-align: middle使用的前提条件是内联元素以及display值为table-cell的元素）。





## 隐藏页面中某个元素的方法

1.`opacity：0`，该元素隐藏起来了，但不会改变页面布局，并且，如果该元素已经绑定 一些事件，如click 事件，那么点击该区域，也能触发点击事件的

2.`visibility：hidden`，该元素隐藏起来了，但不会改变页面布局，但是不会触发该元素已 经绑定的事件 ，隐藏对应元素，在文档布局中仍保留原来的空间（重绘）

3.`display：none`，把元素隐藏起来，并且会改变页面布局，可以理解成在页面中把该元素。 不显示对应的元素，在文档布局中不再分配空间（回流+重绘）






## 用CSS实现三角符号

```css
/*记忆口诀：盒子宽高均为零，三面边框皆透明。 */
div:after{
    position: absolute;
    width: 0px;
    height: 0px;
    content: " ";
    border-right: 100px solid transparent;
    border-top: 100px solid #ff0;
    border-left: 100px solid transparent;
    border-bottom: 100px solid transparent;
}
```




## CSS 盒子模型

CSS 盒模型本质上是一个盒子，它包括：边距，边框，填充和实际内容。CSS 中的盒子模型包括 IE 盒子模型和标准的 W3C 盒子模型。
在标准的盒子模型中，`width 指 content 部分的宽度`。
在 IE 盒子模型中，`width 表示 content+padding+border 这三个部分的宽度`。

故在计算盒子的宽度时存在差异：

**标准盒模型：** 一个块的总宽度 = width+margin(左右)+padding(左右)+border(左右)

**怪异盒模型：** 一个块的总宽度 = width+margin（左右）（既 width 已经包含了 padding 和 border 值）







## 清除浮动的方式

*  添加额外标签

```html
<div class="parent">
    //添加额外标签并且添加clear属性
    <div style="clear:both"></div>
    //也可以加一个br标签
</div>
复制代码
```

*  父级添加overflow属性，或者设置高度
*  建立伪类选择器清除浮动

```css
/* 在css中添加:after伪元素 */
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
