# 一、HTML介绍

- 是超文本语言，是一种标识性的语言，HTML也可称之为元素，不同的标签有不同的功能.
- 一般有一个开始标签和一个结束标签

```html
<!-- 文档类型声明 -->
<!DOCTYPE html>
<!-- 开始标签 -->
<!-- html 根元素 -->
<html lang="en">
<!-- 头部标签 -->
<head>
    <!-- 字符编码格式的声明 -->
    <meta charset="UTF-8">
    <title>标题</title>
</head>
<!-- 文档的主题 -->
<body>
这是我的第一个网页，哈哈
</body>
</html>
<!-- 结束标签 -->
<!-- 标签的特点：标签都是有尖括号包含关键字组成的，有成对的标签，还有单个标签 -->
```

# 二、内联、块级标签

块级标签与内联标签的区别

- 在不设置宽度的情况下块级标签的宽度与浏览器的宽度一致，设置宽高有效，以p标签为例
- 内联标签的宽度和内容有关，但是设置宽高是无效的。以span标签为例。
- 多个块级标签存在的情况下，排列方式从上往下，块级标签是从左往右。
- 块级标签可以包含内联标签，但是内联标签不能包含块级标签，只能包含内联标签。

```html
<!DOCTYPE html>
<html lang="en">

<head>

    <meta charset="UTF-8">
    <title>标题</title>
</head>

<body>
    <!-- 块级标签 -->
    <p style="width: 500px;height: 50px;">故事和酒，淘宝都有
        <!-- 块级标签 -->
        <span style="width: 500px;height: 50px;">故事和酒，淘宝都有</span>
    </p>
    <p style="width: 500px;height: 50px;">故事和酒，淘宝都有</p>
    <!-- 内联标签 -->
    <span style="width: 500px;height: 50px;">
        故事和酒，淘宝都有
        <!-- 块级标签 -->
        <p style="width: 500px;height: 50px;">
            故事和酒，淘宝都有
        </p>
    </span>
</body>
</html>
```

# 三、内联与块级转换

- 块级标签转内联标签，多个块级转化成内联相当于内敛的排列方式，设置宽高无效。设置一个就对着一个生效
- 内联标签转换为块级标签，特点跟块级标签一样。
- 只有块级元素才能设置宽高有效
- 在内联标签中加入内联块元素，就会设置宽高都有效

```html
<!DOCTYPE html>
<html lang="en">

<head>

    <meta charset="UTF-8">
    <title>标题</title>
</head>

<body>
    <!-- 块级标签转内联标签 -->
    <p style="display: inline; height: 50px;">故事和酒，淘宝都有</p>
    <p style="display: inline;">故事和酒，淘宝都有</p>
    <!-- 内联标签转为块级标签 -->
    <span style="display: block;">故事和酒，淘宝都有</span>
    <span style="display: block;">故事和酒，淘宝都有</span>  
     <!-- 内联块元素 -->
    <span style="display: inline-block; height: 50px;">故事和酒，淘宝都有</span>

</body>

</html>
```

# 四、块级标签

```html
<!DOCTYPE html>
<html lang="en">

<head>

    <meta charset="UTF-8">
    <title>标题</title>
</head>

<body>
    <!-- 段落标签 -->
    <p></p>
    <!-- 标题标签，字体逐渐减小 -->
    <h1>故事和酒，淘宝都有</h1>
    <h2>故事和酒，淘宝都有</h2>
    <h3>故事和酒，淘宝都有</h3>
    <h4>故事和酒，淘宝都有</h4>
    <h5>故事和酒，淘宝都有</h5>
    <h6>故事和酒，淘宝都有</h6>

    <!-- 序列标签 -->
    <!-- 有序列表，有1 2 3 这种标识 快捷键 ol>li*3,type设置排列方式-->
    <ol type="A">

        <li>苹果</li>
        <li>香蕉</li>
        <li>草莓</li>
    </ol>
    <!-- 无序列表，type，可以设置有无小黑点 -->
    <ul type="none">
        <li>湾仔</li>
        <li>蒙牛</li>
        <li>伊利</li>
    </ul>

    <!-- 定义列表 ，dt里面就是大的声明-->
    <dl>
        <dt>特色菜</dt>
        <dd>辣椒</dd>
        <dd>方便面</dd>
        <dd>零食</dd>
    </dl>
    <!-- div标签就是一个盒子 -->
    <div style="width: 300px; height: 330px;border: 1px solid red; ">
        
    </div>

</body>

</html>
```

# 五、内联标签

```html
<!DOCTYPE html>
<html lang="en">

<head>

    <meta charset="UTF-8">
    <title>标题</title>
</head>

<body>
    <!-- 内联元素 -->
    <!-- 涉及到了相对路径和绝对路径，有同层级路径 -->
    <!-- 没有这张图片的时候就会提示alt里面的东西，加载错误时才会显示，title表示鼠标停在那里显示的信息 -->
    <!-- <img src="神里凌华.jpg" alt="这是神里菱花" title="图片"> -->
    <!-- 超链接，href里放置的是网址 ,target属性设置的是是否在当前页前打开，_blank：新增一个网页打开-->
    <a href="https://www.baidu.com/" target="_blank">百度一下</a>

    <!-- 实现一键到底部和一键到顶部 -->
    <a href="#bottom" name="top">点我到底部</a>
    <div style="width: 300px;height: 300px;border: 1px solid red;"></div>
    <div style="width: 300px;height: 300px;border: 1px solid red;"></div>
    <div style="width: 300px;height: 300px;border: 1px solid red;"></div>
    <a href="#top" name="bottom">点我到顶部</a>

    <!-- 文本标签 -->
    <span></span>

    <b>我是一段加粗的文字</b>
    <i>我是一段加倾斜的文字</i>

</body>

</html>
```

# 六、html转义

![image-20211112215142618](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20211112215142618.png)

```html
<!DOCTYPE html>
<html lang="en">
<head>

    <meta charset="UTF-8">
    <title>标题</title>
</head>

<body>
    <!-- 表格,border是加上边框 -->
    <table border="1">
        <!-- 创建三行三列的表格，行包含列，th表示的是表头 -->

        <!-- 合并列 colspan=3 -->
        <tr>
            <th colspan="3">数字集合</th>
        </tr>

        <tr>
            <!-- 可以将行合并成一个 -->
            <td rowspan="3">12</td>
            <td>12</td>
            <td>12</td>
        </tr>
        <tr>
            <!-- <td>12</td> -->
            <td>12</td>
            <td>12</td>
        </tr>
        <tr>
            <!-- <td>12</td> -->
            <td>12</td>
            <td>12</td>
        </tr>

    </table>
</body>
</html>
```



# 七、表格和表单

```html
<!DOCTYPE html>
<html lang="en">

<head>

    <meta charset="UTF-8">
    <title>标题</title>
</head>

<body>
    <!-- 表单,action表示的是提交到那个地方去 ,method是提交的方法-->
    <!-- get提交相对不安全但是快，对长度有限制，post提交相对安全，速度较get慢且对长度没有限制，为后端传数据一般用post -->
    <form action="https://www.baidu.com/s" method="post">
        <!-- name属性是一定要的，不加name属性后端无法接收到数据 -->
        <input type="text" name="wd">
        <input type="submit" value="提交"><br>

        <!-- 对下面的内容利用fieldset进行分组 -->
        <fieldset>
            <legend>用户信息</legend>
            <!-- for一定要对应的id属性值，比如用户名，设置为user,这样点击用户名可以跳转到框框里去 -->
            <label for="user">用户名：</label>

            <!-- 文本框 placeholder提示信息,value会自动输入信息-->
            <!-- 当属姓名和属性一致的时候可以只写属性名，readonly是只读的状态 还有disabled禁用-->
            <input type="text" name="user" placeholder="请输入用户名 " value="123" id="user" readonly><br>
            密码：<input type="password" name="pwd" placeholder="请输入密码"><br>
        </fieldset>



        <!-- 单选框,用户选择的不加value属性，后端就无法接受到值 -->
        <input type="radio" name="sex" value="male">男
        <input type="radio" name="sex" value="female">女
        <input type="radio" name="sex" value="weizhi">未知 <br>

        <!-- 复选框,value的作用同单选框 -->
        <input type="checkbox" name="hobby" value="play">玩游戏
        <input type="checkbox" name="hobby" value="study">学习
        <input type="checkbox" name="hobby" value="ball">打球<br>

        <!-- 文件上传accept="image/*"——只能上传图片，如果没有这个属性，那没有限制 -->
        <input type="file" accept="image/*"><br>

        <!-- 下拉框 -->
        <select name="address" id="address">
            <!-- 给选项来一个大的分组 -->
            <optgroup label="dz">
                <option value="HN">湖南</option>
                <option value="M78">浙江</option>
                <option value="JJ">陕西</option>
            </optgroup>
        </select><br>

        <!-- 文本域 -->
        <textarea name="introduce" id="introduce" cols="30" rows="10">

        </textarea><br>

        <!-- 重置，提交 -->
        <input type="reset" value="这是一个重置">
        <input type="submit" value="提交">

        <!-- 按钮也可以进行提交，但是常用的是submit -->
        <button>按钮</button>

        <!-- 不可见的 -->
        <input type="hidden">   


    </form>
</body>

</html>
```

