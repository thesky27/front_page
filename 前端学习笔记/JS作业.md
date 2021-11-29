# 一、实现自定义属性以及属性值

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>标题</title>
    <style>
        
        input,button,#box{
            width: 200px;
            height: 30px;
            margin-top: 20px;
        }
        #box{
            width: 300px;
            height: 300px;
            background-color: blue;
        }
    </style>

</head>

<body>
    <div>

        <label for="shuxing">属&emsp;性</label>
        <input type="text" id="shuxing" placeholder="请输入属性"> <br>
        <label for="shuxingzhi">属性值</label>
        <input type="text" id="shuxingzhi" placeholder="请输入属性值"><br>
        <button>设置属性</button>
    </div>
    <div id="box">
    </div>
    <script>

        var btn = document.getElementsByTagName("button")[0]
        var key = document.getElementById("shuxing")
        var value1 = document.getElementById("shuxingzhi")
        var box = document.getElementById("box")
        btn.onclick=function(){
            box.style[key.value]=value1.value
        }

    </script>
</body>

</html>
```

# 二、设置自动上课时间

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>标题</title>
    <style>
        .word {
            font-size: 24px;
        }

        .time {
            color: red;
        }

        .p1 {
            font-size: 24px;
            color: red;
        }
    </style>

</head>

<body>
    <p>
        <span class="word"></span>
        <span class="time">10</span>
        <span class="word">秒</span>
    </p>
    <p>
        <span class="word"></span>
        <span></span>
    </p>
    <script>
        //定时器一秒钟之后才会执行
        var aspan = document.getElementsByTagName("span")
        var ap = document.getElementsByTagName("p")[0]
        var time = 10  //time到一时清除定时器
        function cdown() {
            if (time > 0) {
                aspan[0].innerText = "距离上课还有"
                aspan[1].innerText = time
                aspan[2].innerText = "秒"
            }else{
                ap.innerText="上课起立"
                ap.className="p1"
                clearInterval(time1)
                clearInterval(time2)
            }
            time--
        }
        cdown()
        var time1 = setInterval(cdown,1000)

        function tidown() {
            var today = new Date()
            var year = today.getFullYear()
            var month = today.getMonth()+1
            var date= today.getDate()
            var hours = today.getHours()
            var minu = today.getMinutes()
            var sec = today.getSeconds()
            if (sec<10) {
                sec = sec+"0"
            }
            if (minu<10) {
                minu = minu+"0"
            }

            aspan[3].innerText="北京时间"+year+"年"+month+"月"+date+"日"
            aspan[4].innerText=hours+":"+minu+":"+sec
        }
        tidown()
        var time2 = setInterval(tidown,1000)

    </script>
</body>

</html>
```

