[TOC]

# HTML

## 块元素

### h1-h5

```markdown
<h1>
    标题1
</h1>
```



### p

```markdown
<p>
    我是一个段落
</p>
```





## 内联元素



### a

```markdown
<a target="_blank" href="xxx.html#test" title="点击调整">链接</a>

* href		链接到某个页面
* title		链接提示
* id  		链接到xxx页面id为test的部分
* target 	在新窗口打开链接

```



### img

```markdown
<img src="image/drinks.gif" width="480" height="800" >

* src 			要展示的图片的存放路径
* alt 			图片内容提示
* width/height 	设定图片宽度/高度，单位是像素
```



### meta

```markdown
<meta charset="utf-8" /> meta标记放在<head>元素中，放在所有其他元素上面

* charset 指定字符集
```



## HTML5

```html
<!doctype html>
```





# CSS

## css样式放在HTML中

```html
<html>
    <head>
        <meta charset="utf-8">
        <title>标题</title>
        <style>
            p {
                
            }
        </style>
    </head>
    <body>
        
    </body>
</html>
```

## 使用link标签

```html
<head>
    ...
    <link type="text/css" rel="stylesheet" href="xxxx.css">
</head>
```





```css
body{
    font-family: sans-serif;
}
h1,h2{
    color: gray;
}
h1 {
    border-bottom: 1px solid black;
}
p {
    background-color: red;
    border: 1px solid gray;
    color: maroon;
}
p.greentea{
    color: green;
}
.greentea{
    color:red;
}

```

* 元素的属性可以从上层属性中==继承==
* 上层属性可以被==覆盖==
* 使用==class==属性可以使同一个元素展示==不同样式==
* 同一个元素可以加入不同的class <p class="greentea blueberry">



#### font

```css
font-family: 'Comic Sans',curive;
font-size:	14px/small/medium;
font-weight:normal;
font-style:italic/oblique;
background-color:rgb(10%,10%,10%);

```

```
下划线、删除线、上划线
text-decoration:underline line-through overline none
```

```
line-height:1.6em
```



#### 元素、盒子

```css
.guarantee {
    line-height:1.9em;
    font-style:italic;
    font-family:Georgia;
    color:#444444;
    border-color:black;
    border-width:1px;
    border-style:solid;
    border-radius:15px;
    border-top/bottom-left/right-radius:3em;
    background-color:#a7cece;
    padding:25px;
    padding-left:80px;
    margin:30px;
    background-repeat:no-repeat;
    background-position:top left;
    background-image:url();
}
使用id配置样式
p#guarantee{
    
}
外边距-边框-内边距-内容区
```



* 样式表顺序很重要，从上到下排列，最下面的样式表最优先





### div

* 可用于页面逻辑分区



### 子孙选择器

```
#guarantee h1{
    
}
div h1{
    
}
```



### span

* 用于内联元素的逻辑分区



### 元素的状态

```
a:link{
    
}
a:visited{
    
}
a:hover{
    
}
```

