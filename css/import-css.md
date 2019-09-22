# css的引入方式

```
参考： 
https://www.cnblogs.com/linga/p/9504147.html
https://www.cnblogs.com/Firesun/p/9713282.html
```



## 1 行内样式
```
<body>
  <div style="color: plum;"></div>
</body>
```

## 2 内部样式表

> style标签写在head里面
```
<style>
  div {
    color: red;
  }
</style>
```

## 3 外部样式表🙋

### 3-1 链接 link.href 
```
<head>
  <link rel="stylesheet" type="text/css" href="../index.css">
</head>
```

### 3-2 引入 @import 🙋
```
<head>
  <style type="text/css">
    @import url("../index.css");
  </style>
</head>
```

### 3-3 二者之间的区别 🙋
> 1 2 3 条对比来看啊

#### 3-3-1 link标签
1. 属于XHTML标签，除了加载CSS外，还可以定义RSS等其他事务。
2. 属于XHTML标签，无兼容性问题。
3. 优先加载CSS文件到页面，以网页文件主体装载前装载CSS文件，因此显示出来的网页从一开始就是带样式的效果的，它不会象导入式那样先显示无样式的网页，然后再显示有样式的网页，这是链接式的优点。
4. 如果通过js来动态引入CSS文件则只能使用链接式。

#### 3-3-2 @import
1. @import属于CSS范畴，只能加载CSS。
2. 属于CSS2.1，低版本的浏览器不支持。
3. @import需要页面网页完全载入以后加载CSS文件。如果网页比较大则会儿出现先显示无样式的页面，闪烁一下。


## 4 优先级
行内样式 > 内部样式 > 外部样式
(后两者按照就近原则，会进行样式的层叠)