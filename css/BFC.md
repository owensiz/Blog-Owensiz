# BFC
```
参考： 
https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Block_formatting_context
https://blog.csdn.net/jiaojsun/article/details/76408215
https://www.jianshu.com/p/0d713b32cd0d
```


## 1 定位方案

### 1-1 普通流 
Normal Flow

行内元素和块级元素，行内元素自左向右，块级元素从上到下

### 1-2 浮动 
Float

印刷中 文本环绕 的概念，先按普通流排列，再浮动

### 1-3 绝对定位
Absolute positioning

脱离普通流，不会对其兄弟元素产生影响


## 2 BFC
Block Formatting Contexts，翻译过来是 块级格式化上下文。

属于上述定位中的普通流，形成一个隔离的封闭盒子容器，BFC内部元素不会对外部元素产生影响。


## 3 BFC的触发
满足如下任一条件即可：
- 常见的： 
    - 根元素或其它包含它的元素：body, html
    - 浮动元素：float 不为 none
    - 绝对定位元素：position 为 absolute, fixed
    - 内联块：display 为 inline-block
    - overflow：overflow 不为 visible; 诸如hidden, auto, scroll
    - display：flow-root
    - 弹性元素：display为 flex 或 inline-flex元素的直接子元素
    - 网格元素：display为 grid 或 inline-grid 元素的直接子元素 
- 不那么常见的：
    - 表格单元块，表格标题，匿名表格单元格元素: display 为 table-cell, table-caption 
    - contain 值为 layout、content或 paint 的元素
    - 多列容器（元素的 column-count 或 column-width 不为 auto，包括 column-count 为 1）
    - column-span 为 all 的元素始终会创建一个新的BFC，即使该元素没有包裹在一个多列容器中（标准变更，Chrome bug）


## 4 BFC的应用
> 使用说明，复制代码去[这里](http://js.jirengu.com/rukex/1/edit)，查看效果。
### 4-1 创建新的BFC来避免外边距折叠（Margin collapsing）的问题。
> 参见 -> demo -> css -> BFC-1.html， 调试css看看
> 当使用overflowd等属性只是为了创建BFC的时候，可能会产生一些其他影响，需要注意。最好写明注释表明目的，以免对后续开发造成误解。
```
<!-- css -->
div{
    width: 100px;
    height: 100px;
    background: lightblue;
    margin: 100px;
}
```
```
<!-- html -->
<body>
    <div></div>
    <div></div>
</body>
```

同一个BFC下会产生外边距折叠。如果想要避免外边距的重叠，可以将其放在不同的 BFC 容器中。

### 4-2 管住子元素的浮动，解决浮动父元素高度坍塌。（使得内部浮动元素保持在内部不乱跑。让浮动内容和周围的内容等高）
> 浮动元素脱离文档流，父元素高度坍塌： 
> 通常的做法是设置父元素 overflow: auto 或者设置其他的非默认的 overflow: visible 的值。
```
<div style="border: 1px solid #000;">
    <div style="width: 100px;height: 100px;background: #eee;float: left;"></div>
</div>
```
> 为父级元素添加属性，overflow: hidden，形成BFC，管住子元素的浮动。
```
<!-- 父级盒子加一句 overflow: hidden; -->
<div style="border: 1px solid #000;overflow: hidden;'">
    <div style="width: 100px;height: 100px;background: #eee;float: left;"></div>
</div>
```

### 4-3 使兄弟元素互不干扰，方便形成两栏布局。（与浮动兄弟元素产生边界）
> 参见 -> demo -> css -> BFC-2.html， 调试css看看

> display: flow-root 一个新的 display 属性值，用于创建无副作用的BFC。在父级块中使用 display: flow-root 可以创建新的BFC。

```
.side-bar{
    width: 100px;
    background-color: plum;
    border: 10px solid tan;
    float: left;
    min-height: 200px;
}
.main {
    background-color: yellowgreen;
    /* float: left; */
    display: flow-root; 
    border: 10px solid tan;
    min-height: 200px;
}
```

```
<body>
  <div class="side-bar"></div>
  <div class="main"></div>
</body>
``` 




> 啊超情绪化