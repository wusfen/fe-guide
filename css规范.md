# 前端规范 - css

css 编写规范。

**目录**
* 文件编码
* 命名规范
* 禁止滥用内联样式
* 禁止用 js 修改样式



## 文件编码
utf-8 (无 bom)



## 命名规范

参考BEM命名改进如下：
```
.blockName-elementName.modifier
```

.modifier (如： active, selected, current 等状态形容词) 禁止单独使用

如禁止这样写：
```
.active{color:red}
```

css命名示例1：
```
.menu
.menu-item
.menu-item.active
```

css命名示例2：
```
.shopCart
.shopCart-title
.shopCart-item
.shopCart-item.selected
```



### 禁止滥用内联样式
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
