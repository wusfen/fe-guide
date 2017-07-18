# 前端规范 - html

html 编写规范。

**目录**
* 文件编码
* 文档声明
* 代码缩进
* 标签
  * 大小写
  * 标签自闭合
  * 标签嵌套
  * 废弃标签
* 属性
  * 大小写
  * 引号
  * 属性书写顺序
  * 布尔值属性
  * 自定义属性
* 图片
* 表单
* 注释
* 引入css
* 引入js
* 禁止使用 table 布局
* 禁止滥用内联样式
* 禁止用 js 修改样式
* 使用模板引擎
* html模板



## 文件编码
utf-8 (无 bom)


## 文档声明
```html
<!DOCTYPE html>
```


## 代码缩进
代码缩进，对齐，尽量语义化，换行，留白。。。


## 标签
标签书写规范

### 大小写
标签名应该小写，不允许大写或大小写混合；  

错误示例：
```html
<DIV clsss="xxx">...</DIV>
```

正确示例：
```html
<div clsss="xxx">...</div>
```

### 标签自闭合
对于无需自闭合的标签，建议不自闭合，  
常见无需自闭合标签有`input`、`img`、`br`、`hr`等  

不建议示例：
```html
<input type="checkbox" value="1" />
```

建议示例：
```html
<input type="checkbox" value="1">
```

### 标签嵌套
* 标签使用必须符合标签嵌套规则。

错误示例：
```html
<a href="xxx">
    a1
    <a href="yyy">a2</a>
</a>

<ul>
    <div></div>
</ul>
```

* 避免过度嵌套。
* 实用为主。

### 废弃标签
禁止使用废弃标签。  
<ul>
    <li><del><code>acronym</code></del> → <ins><code>abbr</code></ins></li>
    <li><del><code>applet</code></del> → <ins><code>object</code></ins></li>
    <li><del><code>b</code></del> → <ins><code>strong</code></ins></li>
    <li><del><code>dir</code></del> → <ins><code>ul</code></ins></li>
    <li><del><code>strike</code></del> → <ins><code>del</code></ins></li>
    <li><del><code>basefont</code></del></li>
    <li><del><code>big</code></del></li>
    <li><del><code>center</code></del></li>
    <li><del><code>font</code></del></li>
    <li><del><code>isindex</code></del></li>
    <li><del><code>tt</code></del></li>
    <li><del><code>u</code></del></li>
</ul>



## 属性
属性书写规范

### 大小写
属性名应该小写，不允许大写或大小写混合。  

错误示例：
```html
<table cellSpacing="0">...</table>
```

正确示例：
```html
<table cellspacing="0">...</table>
```

### 引号
对于属性的定义使用双引号，不允许使用单引号，不允许不使用引号。  

错误示例：
```html
<img class='avatar' src="./img/avatar.png" alt='avatar'>
```

正确示例：
```html
<img class="avatar" src="./img/avatar.png" alt="avatar">
```

### 属性书写顺序
属性建议尽量按照以下给出的顺序依次排列，确保代码的易读性。  
较长的应放较后
* id
* class
* data-*
* type
* src href
* title alt
* ...

### 布尔值属性
布尔类型的属性，建议不添加属性值。  

示例：
```html
<input type="text" disabled>
<input type="checkbox" checked>
```

### 自定义属性
使用自定义属性作为JS的hook，建议以`data-`为前缀。  

示例：

```html
<input data-role="getPic" type="button">
```



## 图片
**【强制】** 禁止 `img` 的 `src` 取值为空；延迟加载的图片也要增加默认的 `src`；

`src` 取值为空，会导致部分浏览器重新加载一次当前页面，参考 [Yahoo performance rules](https://developer.yahoo.com/performance/rules.html#emptysrc)

**【建议】** 为重要图片添加 `alt` 属性；

可以提高图片加载失败时的用户体验。

**【建议】** 添加 `width` 和 `height` 属性，以避免页面抖动；

**【建议】** 有下载需求或者预期会灵活变动的图片采用 `img` 标签实现，无下载需求的图片采用 CSS 背景图实现；

* 用户头像、用户产生的图片等有潜在下载需求的图片，以 img 形式实现，能方便用户下载；
* 无下载需求的图片，比如：icon、背景、代码使用的图片等，尽可能采用 css 背景图实现。



## 表单
**【强制】** 有文本标题的控件必须使用 `label` 标签将其与其标题相关联；

有两种方式：

1. 将控件置于 label 内;
2. label 的 for 属性指向控件的 id。

推荐使用第一种，减少不必要的 id。如果 DOM 结构不允许直接嵌套，则应使用第二种。

示例：

```html
<label><input name="confirm" type="checkbox" value="on"> 我已确认上述条款</label>

<label for="username">用户名：</label> <input id="username" name="username" type="checkbox">
```

**【建议】** 尽量不要使用按钮类元素的 name 属性；

由于浏览器兼容性问题，使用按钮的 name 属性会带来许多难以发现的问题。具体情况可参考 [此文](http://w3help.org/zh-cn/causes/CM2001)；

**【建议】** 在针对移动设备开发的页面时，根据内容类型指定输入框的 `type` 属性；

根据内容类型指定输入框类型，能获得能友好的输入体验。

示例：

```html
<input type="number" value="1">
```



## 注释
**【建议】** 对 **超过10行** 的页面模块进行注释, 以降低开发人员的嵌套成本和后期的维护成本。建议使用结尾注释方式，例如：

当模块代码量较少时，可以省略 `start`。

```html
<!-- 文章内容 start -->
<section id="post">
   do some things...
</section>
<!-- 文章内容 end -->
```

或者标注模块的class或者id：
```html
<!-- #post start -->
<section id="post">
    do some things...
</section>
<!-- #post end -->
```



## 引入css
**【强制】** 引入 CSS 时必须指明 rel="stylesheet"；

建议在 head 中引入页面需要的所有 CSS 资源，因为在页面渲染的过程中，新的CSS可能导致元素的样式重新计算和绘制，页面闪烁；

示例：

```html
<link rel="stylesheet" src="global.css">
```



## 引入js
**【建议】**JavaScript应当放在页面尾部；出于性能方面的考虑，如非必要，请遵守此条建议；

示例：

```html
<body>
    <!-- a lot of elements -->
    <script src="main.js"></script>
</body>
```



## 禁止使用 table 布局
table 用在该用的地方，本身是表示一个表格



## 禁止滥用内联样式
即： 
```html
<div style="xxxx xxxx xxxx xxxx xxxx xxxx xxxx xxxx xxxx xxxx xxxx">
```



## 禁止用 js 修改样式
如：
```javascript
$('.xxx').css({color:red})
```
代替方式：
```javascript
$('.xxx').addClass('error')
```



## 使用模板引擎
禁止在 js 里拼接 html



## html模板
```html
<!DOCTYPE html>
<html lang="zh-cmn-Hans">

<head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
    <meta name="renderer" content="webkit">
    <meta name="viewport" content="width=device-width,initial-scale=1.0,maximum-scale=1.0,user-scalable=no">
    <meta name="MobileOptimized" content="320">
    <meta name="HandheldFriendly" content="true">
    <meta name="full-screen" content="yes">
    <meta name="x5-fullscreen" content="true">
    <meta name="browsermode" content="application">
    <meta name="x5-page-mode" content="app">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black">
    <meta name="format-detection" content="telephone=no">
    <meta name="msapplication-tap-highlight" content="no">
    <title>title</title>
    <link rel="stylesheet" type="text/css" href="css/global.css">
    <link rel="stylesheet" type="text/css" href="css/thisPage.css">
    <style type="text/css">
        /*少量css，不要把所有css写在这*/
    </style>
</head>

<body>
    <div class="container">
        <!-- ... -->
    </div>

    <script src="lib/xx.js"></script>
    <script src="lib/yy.js"></script>
    <!-- ... -->
    <script src="js/global.js"></script>
    <script src="js/thisPage.js"></script>

    <!-- 少量js，可按功能放不同script块里，在前注释功能 -->
    <!-- 功能1 -->
    <script>
        /*...*/
    </script>
    <!-- 功能2 -->
    <script>
        /*...*/
    </script>
</body>

</html>

```


## 参考链接
https://github.com/duowan/fe-guide/blob/master/javascript-guide.md
