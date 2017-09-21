# 前端规范 - js

js 编写规范。

**目录**
* 文件编码
* 代码风格
    * 缩进
    * 引号
    * 命名
    * 注释
* 避免定义全局变量
* 禁止隐性创建全局变量
* 禁止使用 for-in 来遍历数组
* 禁止修改 Object.prototype
* 禁止大量引入第三方插件
* 尽量少在html里写大量js
* 尽可能使用 === 代替 ==
* 基本类型避免 a || b || c
* 禁止用 js 修改样式
* 使用模板引擎


## 文件编码
utf-8 (无 bom)



## 代码风格
编写简洁清晰的代码，代码缩进，对齐，变量命名有意思，换行，留白。。。

### 缩进
代码必须缩进！！ 同一文件缩进格式必须相同。

### 引号
一般情况建议使用单引号。

### 命名
* 变量 camelCase
* 常量 CONST_NAME
* 类，构造函数 CamelCase

### 注释
* 文件注释
    在文件头部注释，用途、创建时间、修改时间、作者
* 函数注释
    在函数前注释，功能、输入类型，输出类型
* 变量注释
    在关键变量前注释
* 其它关键点必须注释



## 避免定义全局变量
禁止示例：
```javascript
// global scope

var name = 'wsf';
```

避免方式 IIFE(Immediately-Invoked Function Expression)
```javascript
!(function(){

    var name = 'wsf';
    // ...

})();
```



## 禁止隐性创建全局变量
禁止示例：
```javascript
!(function(){


    global = 'global';
    // ...

})();
```
局部变量使用使用 var 定义， es6 let



## 禁止使用 for-in 来遍历数组
禁止示例：
```javascript
for(var i in array){
    // array[i]
}
```
代替方式：
```javascript

for(var i=0; i<array.length; i++){
    // array[i]
}
```



## 禁止修改 Object.prototype
Array.prototype 可以用来兼容 map, filter 等方法，所以禁止使用 for-in 来遍历数组



## 禁止大量引入第三方插件
自己能完成的功能避免引用插件，
控制引用插件的数量，来源是否安全，质量是否良好，文件大小是否过大



## 尽量少在html里写大量js
静态html除外


## 禁止在js里拼接html
禁止示例：
```javascript

    // ...
    var html = '<ul class="xxx">';
    for(var i=0; i<list.length; i++){
        html+= '<li class="xxx-item">' + list[i].name + '</li>';
    }
    html+='</ul>';
    // ...

```
代替方式：
使用模板引擎或mvvm框架，如vue


## 尽可能使用 === 代替 ==
基本类型判断相等应使用 ===，
== 容易造成自动转换的误判 0, '', undefined, null, false


## 基本类型避免 a || b || c
容易造成逻辑为 false 的误判 0, '', undefined, null, false
基本类型判断 undefined
```javascript
if(a === undefined){
    //...
}
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


