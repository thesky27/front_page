# 一、CSS介绍

- css:层叠样式表，可以用来修饰静态网页 ，可以配合各种脚本对网页进行格式化
- 是网页的化妆师，让页面变得更加美观
- 使用方法
  1. 直接写在标签里
  2. 写在style标签中
  3. 使用外部.css文件

# 二、使用css的方法

```html
<!DOCTYPE html>
<html lang="en">

<head>

    <meta charset="UTF-8">
    <title>标题</title>

<!-- 内部样式,在head里面的style里面写 -->
    <style>
        span{
            color: gray;
            font-size: 40px;
        }
        
    </style>

<!-- 通过link标签来引用·css样式，rel定义的是要加载的样式表，href里面添加的是相对路径（绝对路径也是可以的） -->
    <link rel="stylesheet" href="">
</head>


<body>
<!-- 行内样式 ，颜色与字体大小之间要用字体隔开-->
<p style="color: rebeccapurple; font-size: 24px;">这个五一你打算去哪里玩</p>
<span>今天晚上有点冷</span>
</body>

</html>
```

- 行内样式的优先级最大的大于内部样式，大于外部样式
- 内部样式与外部样式的优先级是一样的，遵循就近原则，近水楼台先得月

# 三、css选择器

### 3.1简单选择器

```html
<!DOCTYPE html>
<html lang="en">

<head>

    <meta charset="UTF-8">
    <title>标题</title>

    <style>
        /* 标签选择器 */
        p{
            color: hotpink;
            font-size: 40px;
        }
        /* <!-- id选择器,用井号来表示 --> */
        #p2{
            color: khaki;
        }
        /* class选择器 ,用.来表示*/
        .p3{
            color: lawngreen;
        }    
    </style>
    
</head>

<body>
<p id="p1">这个五一你打算去哪里玩</p>
<p id="p2">这个五一你打算去哪里玩</p>
<p class="p3">这个五一你打算去哪里玩</p>
<p class="p3">这个五一你打算去哪里玩</p>

</body>

</html>
```

- id选择器和class选择器优先级大于标签选择器，标签选择器的优先级是最低的
- id的优先级大于class选择器，没有遵循就近原则。
- 还有一个全选选择器，他的优先级是最低的

### 3.2复杂选择器

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>标题</title>

    <style>
        /* 群组选择器,群组选择器可以将标签选择器和class选择器以及id选择器结合起来 */
        div,
        p {
            color: lawngreen;
            font-size: 40px;
        }

        /* 后代选择器，子代选择器,大于的意思就是他里面的元素 */
        div>span {
            /* 只包含他的儿子，就像div下的p下的span不会加上此样式 */
            color: red;
        }

        /* 后代选择器 ，用空格隔开，只要是他里面元素，都会改变颜色*/
        div span {
            color: blue;
        }

        /* 兄弟选择器 ,给p1的兄弟加上颜色，但是也是遵循就近原则，第一个p不会加*/
        #p1~p {
            color: brown;
        }

        /* 相邻选择器 ,给与它相邻的选择器加上颜色，但是也是遵循就近原则*/
        #p1+p {
            color: gold;
        }
        /* 属性选择器 */
        p[name="p22"]{
            font-size: 60px;
            color: indigo;
        }
    </style>

</head>

<body>
    <div>晚上我要节食</div>
    <p>你将造你的城邦，在废墟之上</p>


    <div>
        <p>
            我是div里面的第一个p标签
        </p>
        <p id="p1">
            我在div标签里面，是第二个p标签 <br>
            <span>
                我是div标签里的p标签里面的span标签
            </span>
        </p>
        <p>我是p的兄弟</p>
        <p>我是p的兄弟</p>
        <p>我是p的兄弟</p>
        <span>
            我是结尾的span标签
        </span>
    </div>
    <span>
        <p name="p22">
            这是属性选择器
        </p>
    </span>
</body>

</html>
```

- 复杂选择器遵循就近原则，也遵循从上往下执行的原则

**伪类选择器**

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>标题</title>
    <!-- 伪类选择器 -->
    <style>
        /* <!-- 未选中时的状态 --> */
        a:link{
            color: yellow;
        }
        /* 鼠标悬浮时的状态 */
        a:hover{
            color: blue;
        }
        /* 点击激活时的状态 */
        a:active{
            color: gray;
        }
        /* 访问之后的状态 */
        a:visited{
            color: red;
        }
    </style>

</head>
<body>
    <a href="#">百度一下</a>
</body>

</html>
```

