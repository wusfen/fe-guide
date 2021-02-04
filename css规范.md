# 前端规范 - css

css 编写规范。

**目录**
* 文件编码
* 选择器
* 属性顺序
* 禁止滥用内联样式
* 禁止用 js 修改样式



## 文件编码
utf-8 (无 bom)



## 选择器

使用嵌套与 dom 结构保持一致。结构清晰语义明确（注：选择器无需优化，与性能关系小到可以完全忽略）
```less
// less, scss [scope]
.page {
  header{
    section.user{
      img.avatar{}
      span.username{}
    }
  }
  main{
    section.xxx{}
    section.yyy{}
  }
  footer{}
}
```

## 属性顺序
```

// 与父级关系
flex
order
  
// 布局
content
position
top
left
right
bottom
display
align-items
justify-content

// 盒子模型
width
height
margin
padding
border
border-radius

// 自身样式
background
box-shadow
color

// 字体
text-align
font
line-height
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
