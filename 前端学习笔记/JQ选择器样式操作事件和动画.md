# Jquery框架

### 一、JQuery介绍

- JQuery是一个JavaScript库，也是一个js文件，里面封装了很多的方法
- 进入下面的网址，搜索JQuery就可以了

[BootCDN - Bootstrap 中文网开源项目免费 CDN 加速服务](https://www.bootcdn.cn/)

- 两种引用方式
  - 一种是直接复制script标签粘贴在body里面
  - 另一种就是复制代码，然后引入。

### 二、jQuery基础使用

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>标题</title>
    <style>
    </style>

</head>
<body>
<p class="p1">我是段落标签一</p>
<p class="p1">我是段落标签二</p>

<ul>
    <li>1</li>
    <li>2</li>
    <li>3</li>
</ul>

    <script src="https://cdn.bootcdn.net/ajax/libs/jquery/3.6.0/jquery.js"></script>
    <!-- 所有的scrip代码都要在这之下写，才能jQuery生效 -->
    <script>
        // jQuery选择器
        // $(function () {
        //     alert("三个")
        // })
        //正常来写的
        var ap1 = document.getElementsByClassName("p1")
        // ap1[0].innerText="今天天气真好"

        //jq获取元素，不需要加索引时全部修改，需要加索引时用eq
        // $(".p1").text("今天天气有点热")
        $(".p1").eq(1).html("<h1>今天天气有点热</h1>")

        // js转化为jq
        $(ap1).eq(0).text("三个一下")

        //jq转化为js
        var ap2 = $(".p1")
        ap2[0].innerHTML="**三和**"
        ap2.get(1).innerText="哈哈哈哈"

        //jQuery可以同时修改多条数据，而js代码只能修改一条

        //each
        $("ul li").each(function () {
            //获取元素的内容，获取元素下标就是index
            console.log($(this).text());
            console.log(this.text());
        })


    </script>
</body>

</html>
```

### 三、jQuery操作HTML属性

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>标题</title>
    <style>
        .div1{
            width: 300px;
            height: 300px;
            background-color: red;
        }
        div{
            width: 300px;
            height: 300px;
            background-color: green;
        }
    </style>

</head>
<body>
<div></div>
<button>按钮1</button>
<button>按钮2</button>
<button>按钮3</button>
<button>按钮4</button>
<input type="text" name="user" id="" value="">
    <script src="https://cdn.bootcdn.net/ajax/libs/jquery/3.6.0/jquery.js"></script>
    <!-- 所有的scrip代码都要在这之下写，才能jQuery生效 -->
    <script>
        //jquery操作class属性,以及属性值
        //添加class属性
        $('button').eq(0).click(function () {
            //点击就增加样式，两个是继续添加而js则是有则改
            $("div").addClass("div1")    
            // $("div").addClass("div2")    
        })
        //删除class属性
        $('button').eq(1).click(function () {
            //点击就删除样式
            $("div").removeClass("div1")    
        })
        //删除属性和属性值
        $('button').eq(2).click(function () {
            //点击就删除属性以及属性值，传的是属性
            $("div").removeAttr("class")    
        })

        //attr 无则增有则改
        $('button').eq(3).click(function () {
            //最终显示的是div2属性，可以添加任何属性比如id，name等
            $("div").attr("class","div1")    
            $("div").attr("class","div2")    
        })

        //jQuery获取元素的值val,默认获取元素第一个值,也是通过下标获取值
        console.log($("input").val());
        //修改值的时候就是遍历修改


        


    </script>
</body>

</html>
```

### 四、jQuery修改CSS样式

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>标题</title>
    <style>
        div {
            width: 300px;
            height: 300px;
            border: 3px solid red;
            background-color: green;
            padding: 5px;
        }
        .div1{
            width: 300px;
            height: 300px;
            border: 3px solid green;
            background-color: red;
            padding: 5px;
            position: relative;
        }
        .div2{
            width: 100px;
            height: 100px;
            border: 3px solid green;
            background-color: blue;
            padding: 5px;
        }

    </style>

</head>

<body>
    <div class="div1">
        <div class="div2"></div>
    </div>

    <script src="https://cdn.bootcdn.net/ajax/libs/jquery/3.6.0/jquery.js"></script>
    <!-- 所有的scrip代码都要在这之下写，才能jQuery生效 -->
    <script>
        //jquery获取元素的宽高
        console.log($("div").width());//获取盒子的宽度，但是只能获取到本身所涉及到的元素。
        console.log($("div").innerWidth());//获取盒子的宽度加上了内边距的宽度
        console.log($("div").outerWidth());//获取盒子的宽度加上了内边距的宽度,加上边框，也就是盒子的全部宽度
        //jq修改样式
        // $("div").css("background", "red")
        // $("div").css({
        //     //属性：值
        //     "width": "400px",
        //     "height": "200px"
        // })

        //定位元素,父级元素一定要有定位，否则就是定位浏览器窗口
        console.log($(".div2").position());
        //定位浏览器窗口
        console.log($(".div2").offset());

    </script>
</body>

</html>
```

### 五、jQuery事件

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>标题</title>
    <style>
        div {
            width: 300px;
            height: 300px;
            border: 3px solid red;
            background-color: green;
            padding: 5px;
        }
    </style>

</head>

<body>
    <div class="div1">
    </div>
    <button>按钮</button>
    <p>我是段落一</p>
    <p>我是段落二</p>

    <script src="https://cdn.bootcdn.net/ajax/libs/jquery/3.6.0/jquery.js"></script>
    <!-- 所有的scrip代码都要在这之下写，才能jQuery生效 -->
    <script>

        //事件
        //点击一次就打印一个一
        $("div").click(function () {
            console.log(1);
        })
        //双击一次就打印一个2
        $("div").dbclick(function () {
            console.log(2);
        })
        //划入事件,划入打印一个三
        $("div").mouseenter(function () {
            console.log(3);
        })
        //划入事件,划入打印一个四
        $("div").mouseleave(function () {
            console.log(4);
        })

        //划入打印5，划出打印6,如果只有一个事件那么不管划入还是划出都会执行一个功能
        $("div").hover(function () {
            console.log(5);
        }, function () {
            console.log(6);
        })

        //绑定事件
        $("button").click(function () {
            //  on 表示要添加的功能
            $("p").on("click", function () {
                $("p").css("background", "red")
            })
        })
        //绑定多个事件
        $("p").on({
            "mouseenter": function () {
                $(this).css('background', "red")
            },
            "mouseleave": function () {
                $(this).css('background', "blue")
            },
        })

        //清除事件，但是不会清除事件之前的功能,默认清楚所有的样式
        $("button").click(function () {
            $("p").off("mouseenter")
            $("p").off()
            $("p").css("background", "transparent")

        })
    </script>
</body>

</html>
```



### 六、jQuery动画

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>标题</title>
    <style>
        div {
            width: 300px;
            height: 300px;
            border: 3px solid red;
            background-color: green;
            padding: 5px;
            position: relative;
        }
    </style>

</head>

<body>
    <div class="div1">
    </div>
    <button>隐藏按钮</button>
    <button>显示按钮</button>
    <button>取反按钮</button>
    <button>淡出按钮</button>
    <button>淡入按钮</button>
    <button>取反按钮</button>
    <button>动画按钮</button>
    <button>停止按钮</button>

    <script src="https://cdn.bootcdn.net/ajax/libs/jquery/3.6.0/jquery.js"></script>
    <!-- 所有的scrip代码都要在这之下写，才能jQuery生效 -->
    <script>

        //隐藏效果
        $("button").eq(0).click(function () {
            //将会在2秒内进行隐藏
            $("div").hide(2000) 
            $("div").slideUp(2000) 
        })
        //显示效果
        $("button").eq(1).click(function () {
            //让原本的hide方法隐藏的展示出来
            $("div").show(2000) 
            $("div").slideDown(2000) 
        })
        
        //取反显示
        $("button").eq(2).click(function () {
            //让原本的hide方法隐藏的展示出来,隐藏的显示
            $("div").slideToggle(2000) 
            //对角的方式进行
            $("div").toggle(2000) 
        })
        //淡出显示
        $("button").eq(3).click(function () {
            $("div").fadeOut(2000) 
        })
        //淡入显示
        $("button").eq(4).click(function () {
            $("div").fadeIn(2000) 
        })
        //取反显示
        $("button").eq(5).click(function () {
            $("div").fadeToggle(2000) 
        })

        //动画效果,所有元素默认都是静态定位,改变定位之后才会有移动的效果
        $("button").eq(6).click(function () {
            $("div").delay(3000).animate({
                "width":"300px",
                "height":"300px",
                "top":"50px",
                "left":"60px",
            })
        })
        //停止动画
        $("button").eq(7).click(function () {
            $("div").stop()
        })
    </script>
</body>

</html>
```

