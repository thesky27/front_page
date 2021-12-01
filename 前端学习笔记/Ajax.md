# Ajax

### 一、JSON格式

- 本质上是一个字符串，是作为数据交换的格式。主要是用于前后端数据交互
- json可以是对象，数组，字符串，

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
    

    <script src="https://cdn.bootcdn.net/ajax/libs/jquery/3.6.0/jquery.js"></script>
    <!-- 所有的scrip代码都要在这之下写，才能jQuery生效 -->
    <script>
        //json格式——特殊格式的字符串,
        var str1 = '{"name":"北斗"}'
        //分为两种类型：json对象，json数组,可以是数值null数组对象
        var obj1 = '{"name":"北斗","age":"18"}'//json对象
        var obj2 = '["name","北斗","age","18"]'//json数组
        var str2 = {"name":"北斗","age":18}
        console.log(obj1["name"]);//北斗
        console.log(obj2["name"]);//undefiend

        // js对象转json
        var obj4 = JSON.stringify(str2)
        console.log(obj4);
        // json转js对象,得到了对象
        var obj3 = JSON.parse(str1)
        console.log(obj3);
    </script>
</body>

</html>
```



### 二、Ajax的使用

- 异步请求，可以只请求页面中的一部分，并不是全部，
- 同步请求是传统的请求方式，一步出错，就刷新不出来了。

1.py文件的准备

```python
import tornado.ioloop
import tornado.web

    class MainHandler(tornado.web.RequestHandler):
        def get(self):
            self.write("Hello, world")
            #渲染前端页面
            self.render("前端学习.html")
        def post(self):
            #传的是name属性，获取数据
            self.get_argument("user")
            self.get_argument("pwd")

    if __name__ == "__main__":
        application = tornado.web.Application([
            (r"/", MainHandler),
        ])
        application.listen(8888)
        tornado.ioloop.IOLoop.current().start()
```

2.py文件的准备

```python
import tornado.ioloop
import tornado.web

    class MainHandler(tornado.web.RequestHandler):
        def get(self):
            self.write("Hello, world")
            #渲染前端页面
            self.render("前端学习.html")
        def post(self):
            #传的是name属性，获取数据
            a =int(self.get_argument("aa"))
            b = int(self.get_argument("bb"))
            c = a+b
            #将结果写入到前端
            r_data = {"cc":c}
            self.write(r_data)
            

    if __name__ == "__main__":
        application = tornado.web.Application([
            (r"/", MainHandler),
        ])
        application.listen(8888)
        tornado.ioloop.IOLoop.current().start()
```

html文件

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


    <form action="/" method="post">
        <!-- 传统的前后端数据交互 -->
        用户名：<input type="text" name="user" id="">
        密&emsp;码 <input type="text" name="pwd">
        <input type="submit" value="提交">
    </form>

    <input type="text">+<input type="text">=<input type="text">
    <input type="submit" value="">
    <script src="https://cdn.bootcdn.net/ajax/libs/jquery/3.6.0/jquery.js"></script>
    <script>
        var apint = $("input")
        apint.eq(6).click(function () {
            var a = apint.eq(4).val
            var b = apint.eq(5).val

            $.ajax({
                "type": "post",//提交方式
                "url": "/",//提交路径
                "data": {
                    "aa": a,
                    "bb": b
                },
                //成功返回调用函数
                "success":function(data){
                    var c = data['cc']
                    apint.eq(6).val(c)
                },
                "error":function (error) {
                    console.log(error);
                }
            })
        })
    </script>
</body>

</html>
```

### 三、HTML标签的补充

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

<input type="email" name="" id=""> 邮件 <br>
<input type="url" name="" id="">  网址 <br>
<input type="number" name="" id=""> 数值 <br>
<input type="tel" name="" id="">   电话 <br>
<input type="date" name="" id="">  时间 <br>

<!-- controls视频播放控件，autoplay视频自动播放 ,muted静音播放k,loop循环播放,poster播放前的图片-->
<video src="01.mp4" controls autoplay muted loop poster="01.png"> </video> 视频

<video src="">
    <source src="01.mp4" type="video/mp4">
    <source src="01.ogg" type="video/ogg">
</video>

</body>

</html>
```

### 四、自动轮播实现

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>标题</title>
    <style>
        /* 轮播图的样式 */
        .lunbo {
            width: 440px;
            height: 433px;
            position: relative;
            border: 1px solid gray;
        }

        .pic {
            position: absolute;
        }

        .btn li {
            position: absolute;
            width: 50px;
            height: 50px;
            top: 50%;
            /* background-color: red; */
            line-height: 50px;
            /*垂直居中*/
            text-align: center;
            /*水平居中*/
            font-size: 30px;
        }

        .left {
            left: 0;
        }

        .right {
            right: 0;
        }


        .table {
            position: absolute;
            bottom: 5px;
            left: 50%;
            transform: translateX(-50%);
        }

        .table li {
            float: left;
            width: 10px;
            height: 10px;
            border: 1px solid red;
            background-color: red;
            border-radius: 50%;
            margin-left: 8px;
        }

        .table li:hover {
            background-color: orange;
            border: 1px solid blue;
        }

        .table li .on {
            background-color: red;
            border: 1px solid skyblue;
        }
        .pic li{
            position: absolute;
        }
    </style>
    <link rel="stylesheet" href="clear.css">
</head>

<body>
    <!-- 轮播图 -->
    <div class="lunbo">
        <!-- 图片区域 -->
        <ul class="pic">
            <li><img src="01.png" alt=""></li>
            <li><img src="02.png" alt=""></li>
            <li><img src="03.png" alt=""></li>
            <li><img src="04.png" alt=""></li>
        </ul>
        <!-- 左右箭头区域 -->
        <ul class="btn">
            <li class="left">&lt;</li>
            <li class="right">&gt;</li>
        </ul>
        <!-- 小圆点区域 -->
        <ul class="table">
            <li></li>
            <li></li>
            <li></li>
            <li></li>
        </ul>
    </div>
    <script src="https://cdn.bootcdn.net/ajax/libs/jquery/3.6.0/jquery.js"></script>
    <script>

        //获取元素
        var apic = $(".pic li")
        var aptn = $(".btn li")
        var atab = $(".tab li")

        //初始化
        //只显示第一张图片
        apic.hide.eq(0).show()
        atab.removeAttr("class").eq(0).addClass("on")
        var first = 0
        function change(i) {
            apic.eq(first).fadeOut(1000)
            atab.eq(first).removeAttr("class")
            first = i //全局变量
            apic.eq(first).fadeIn(1000)
            atab.eq(first).addClass("on")
        }
        //点击小圆点进行切换
        atab.click(function () {
            var num = $(this).index
            if (num != first) {
                change(num)
            }
        })
        aptn.click(function () {
            var num = first
            if ($(this).index) {
                num += 1
                if (num > (apic.length - 1)) {
                    num = 0
                }
            } else {
                num -= 1
                if (num < 0) {
                    num = apic.length - 1
                }
            }
            change(num)
        })
        //自动轮播
        function auto() {
            time = setInterval(function () {
                var num = first
                num++
                if (num > (apic.length - 1)) {
                    num = 0
                }
                change(num)
            }, 3000)
        }
        auto()

        //鼠标划入暂停轮播,划出继续轮播
        $("div").hover(function () {
            clearInterval(time)
        },function () {
            auto()
        })
    </script>
</body>

</html>
```

### 五、Ajax的使用

**传统的前后端数据交互**

py文件的准备

```python
import tornado.ioloop
import tornado.web

    class MainHandler(tornado.web.RequestHandler):
        def get(self):
            self.render("Ajax.html")
        def post(self):
            #接受前端的数据，这是传统的交互
            self.get_argument("user")
            self.get_argument("pwd")
            self.get_argument("sex")
            self.get_arguments("hobby")
            self.get_argument("file")
            self.get_argument("adress")
            self.get_argument("intro")

            

    if __name__ == "__main__":
        application = tornado.web.Application([
            (r"/", MainHandler),
        ])
        application.listen(8888)
        tornado.ioloop.IOLoop.current().start()
```

HTML文件

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>标题</title>

</head>

<body>
    <form action="/" method="post">
       
        用户名：<input type="text" name="user" id=""> <br>
        密&emsp;码 <input type="text" name="pwd"> <br>
        <input type="radio" name="sex" value="male">男
        <input type="radio" name="sex" value="female">女
        <input type="radio" name="sex" value="weizhi">未知 <br>

        <input type="checkbox" name="hobby" id="" value="play">玩游戏
        <input type="checkbox" name="hobby" id="" value="playball">打篮球
        <input type="checkbox" name="hobby" id="" value="study">学习 <br>
        <input type="file" name="file" id="" value="file"> <br>
        
        <select name="adress" id="adress">
            <option value="bj">备件</option>
            <option value="sh">上海1</option>
            <option value="gz">广州</option>
        </select> <br>
        <textarea name="intro" id="" cols="30" rows="10"></textarea>
        <input type="submit" value="提交">
        <input type="reset" value="取消">
    </form>
    

</form>

</body>

</html>
```

**Ajax数据交互**

py文件的准备

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>标题</title>

</head>

<body>


    用户名：<input type="text" name="user" id=""> <br>
    密&emsp;码 <input type="text" name="pwd"> <br>
    <input type="radio" name="sex" value="male">男
    <input type="radio" name="sex" value="female">女
    <input type="radio" name="sex" value="weizhi">未知 <br>

    <input type="checkbox" name="hobby" id="" value="play">玩游戏
    <input type="checkbox" name="hobby" id="" value="playball">打篮球
    <input type="checkbox" name="hobby" id="" value="study">学习 <br>
    <input type="file" name="file" id="" value="file"> <br>

    <select name="adress" id="adress">
        <option value="bj">备件</option>
        <option value="sh">上海1</option>
        <option value="gz">广州</option>
    </select> <br>
    <textarea name="intro" id="" cols="30" rows="10"></textarea>
    <button>登录</button>
    <input type="reset" value="取消">



    <script src="https://cdn.bootcdn.net/ajax/libs/jquery/3.6.0/jquery.js"></script>
    <!-- 所有的scrip代码都要在这之下写，才能jQuery生效 -->

    <script>

        var btn = $("button")
        btn.click(function () {
            var user = $("input[name='user']").val()
            var pwd = $("input[name='pwd']").val()
            var sex = $("input[name='sex']:checked").val()
            var hobby = $("input[name='sex']:checked").map(function () {
                return $(this).val()
            }).get().join(',') //把所有返回的值放到数组里面。
            var file = $("input[name='file']").val()
            var adress = $("select").val()
            var intro = $("textarea").val()
        })

        $.ajax({
            "type":"post",
            "url":"/",
            "data":{
                "user":user,
                "pwd":pwd,
                "sex":sex,
                "hobby":hobby,
                "file":file,
                "adress":adress,
                "intro":intro,
            }
        })
    </script>
</body>

</html>
```

