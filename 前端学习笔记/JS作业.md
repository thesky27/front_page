实现自定义属性以及属性值。

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

