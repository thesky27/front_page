# CSS提升

### 1.盒子模型

- 包含边距，边框，填充和实际内容
- margin——外边距，盒子与盒子之间的距离，border——边框，
- padding——内边距，盒子与内容之间的距离，content——内容
- 一个盒子的大小是由内容，内边距和边框组成。

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>标题</title>
 
 <style>
     /* 盒子模型大小：内容加上边框 */
    div{
        width: 300px;
        height: 300px;
        background-color:wheat;
        /* 边框：大小，样式，颜色
        border: 5px solid red; */
        /* 单独加颜色是不能显示出来的 */
        /* border-color: skyblue; */
        /* 大小，还是没有效果 */
        /* border-width: 10px; */
        /* 样式 */
        /* border-style: groove; */
        border-top:5px solid red;
        border-bottom:5px solid yellow;
        border-left:5px solid slateblue;
        border-right:5px solid greenyellow;

        /* 边框弧度 */
        border-radius: 8px;


    }
 </style>
</head>
<body>
<div></div>
</body>

</html>
```

内边距和外边距

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>标题</title>
 
 <style>
     /* 盒子模型大小：内容加上边框 ,内边距*/
    .div1{
        width: 300px;
        height: 300px;
        background-color:wheat;
        /* 边框：大小，样式，颜色*/
        border: 5px solid red; 
        /* 内边距 */
        /* padding: 10px; */

        /* 简单样式 */
        padding-left: 20px;
        padding-top: 10px;
        padding-right: 20px;
        padding-bottom: 40px;
        /* 复合样式：一个参数是上下左右，两个参数是上下，左右，三个参数是：上  左右  下，四个参数：上右下左 */
        padding: 10px 20px 30px 40px;
        /* 设置外边距，复合样式的话关系是跟内边距一模一样的 */
        margin-bottom: 50px;
    }
    .div2{
        width: 300px;
        height: 300px;
        background-color:wheat;
        /* 边框：大小，样式，颜色*/
        border: 5px solid blue; 
        margin-top: 50px;
    }
    /* 如果两个盒子之间都设置了外边距，只会取最大的那个距离 */
 </style>
</head>
<body>
<div class="div1"></div>
<div class="div2"></div>
</body>

</html>
```



### 2.CSS浮动

- 让原本的盒子脱离文档流，会产生浮动坍塌的问题
- 在父元素不设置高度的情况下，父元素的高度由子元素撑起来的。
- 子元素浮动起来的时候，父元素将会没有高度。
- 解决浮动坍塌的问题
  1. 给父元素加上高度
  2. 加空盒子
  3. 在父元素里面加入overflow：hidden
  4. 加上伪元素，默认会是行内元素

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>标题</title>
 <style>
     /* 加上浮动的元素会变成内联块元素，设置宽高有效，排列方式左右排列 */
    .div1{
        width: 300px;
        height: 300px;
        background-color:red;
        /* 加上浮动,结果只能看到红色盒子和蓝色盒子，三维世界，想想浏览器有高度，浮动的那个高度坐标升高 */
        float: left;
    }
    .div2{
        /* 两个盒子加上浮动之后就会显示红色和绿色 */
        float: left;
        width: 300px;
        height: 300px;
        background-color:green;
    }
    .div3{
        width: 300px;
        height: 300px;
        background-color:blue;
        float: left;
    }
    .div4{
        width: 300px;
        height: 300px;
        background-color:purple;
    }
    .box{
        /* 给父元素加高度，但是情况不太理想 */
        /* height: 300px; */
        /* 超出部分隐藏 */
        /* overflow: hidden; */
        /*  */
    }
    /* 加上空盒子，不太推荐 */
    /* .div5{
        height: 300px;
    } */
    /* 加上伪元素 */
    .box:after{
        display: block; /*设置成块级元素*/
        content: '';
        clear: both;
    }
    

 </style>
</head>
<body>
<div class="box">
    <div class="div1"></div>
    <div class="div2"></div>
    <div class="div3"></div>
    <div class="div5"></div>
 
</div>
<div class="div4"></div>
</body>

</html>
```



### 3.CSS定位

静态定位——静态定位,了解就可以了

相对定位——相对定位,以自身作为参照物来移动的，相对定位不会改变文档流

父相子绝——子元素设置绝对定位之后，会依次网上找父级有没有相对定位，如果有则就以该级为参照做偏移，如果都没有则会以浏览器为参照物。

但是父相子绝会脱离文档流，

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>标题</title>
    <style>
        /* 默认的遵循是静态定位 */
        .div3{
            width: 100px;
            height: 100px;
            background-color: coral;
            position: fixed;
        }
        .box{
            width: 300px;
            height: 300px;
            background-color:silver;
            border:2px solid skyblue;
            /* 相对定位 */
            position: relative;
            margin-top: 10px;
        }
        
        .div1{
            width: 100px;
            height: 100px;
            background-color: royalblue;
            /* 绝对定位 */
            position: absolute;
            top: 10px;
        }
        .div2{
            width: 100px;
            height: 100px;
            background-color: green;
        }
        /* 固定定位：参照物永远都是浏览器的窗口,可以做广告的窗口 */
        

    </style>
</head>

<body>
    <div class="div3"></div>
    <div class="box">
        <div class="div1"></div>
        <div class="div2"></div>
        
    </div>
    
    <div class="box"></div>
    <div class="box"></div>
    <div class="box"></div>
    <div class="box"></div>
    <div class="box"></div>
    <div class="box"></div>
    <div class="box"></div>
    
</body>

</html>
```



### 4.重置样式,层级

```css
/* http://meyerweb.com/eric/tools/css/reset/ 
   v2.0 | 20110126
   License: none (public domain)
*/

html, body, div, span, applet, object, iframe,
h1, h2, h3, h4, h5, h6, p, blockquote, pre,
a, abbr, acronym, address, big, cite, code,
del, dfn, em, img, ins, kbd, q, s, samp,
small, strike, strong, sub, sup, tt, var,
b, u, i, center,
dl, dt, dd, ol, ul, li,
fieldset, form, label, legend,
table, caption, tbody, tfoot, thead, tr, th, td,
article, aside, canvas, details, embed, 
figure, figcaption, footer, header, hgroup, 
menu, nav, output, ruby, section, summary,
time, mark, audio, video {
	margin: 0;
	padding: 0;
	border: 0;
	font-size: 100%;
	font: inherit;
	vertical-align: baseline;
}
/* HTML5 display-role reset for older browsers */
article, aside, details, figcaption, figure, 
footer, header, hgroup, menu, nav, section {
	display: block;
}
body {
	line-height: 1;
}
ol, ul {
	list-style: none;
}
blockquote, q {
	quotes: none;
}
blockquote:before, blockquote:after,
q:before, q:after {
	content: '';
	content: none;
}
table {
	border-collapse: collapse;
	border-spacing: 0;
}
```

- 上面的可以放在一个css文件里面，用来清除浏览器自带的样式,
- 在style里面用link引入css文件生效

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>标题</title>
    <style>

            li{
                width: 100px;
                height: 100px;
                list-style: none;
            }
            .li1{
                background-color: red;
                position: absolute;
                /* 加上层级,层级数越大，就能显示出来，用来适合做轮播图 */
                z-index: 2;
            }
            .li2{
                background-color: green;
                position: absolute;
            }
            .li3{
                background-color: blue;
                position: absolute;
            }
            ul{
                position: relative;
            }

    </style>
</head>

<body>
<ul>
    <li class="li1"></li>
    <li class="li2"></li>
    <li class="li3"></li>
</ul>
    
    
</body>

</html>
```

