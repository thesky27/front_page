# JavaScript基础

### 一、三种书写方式

1. 可以写在head头部里面。
2. 写在body标签里面
3. 通过js文件来引入使用

如果写在头部标签里，要加上windowonload这个

**一般不会写在head里面，因为执行顺序是从上向下执行的**

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>标题</title>

</head>

<body>
    <button>按钮</button>
    可以通过引入的方式来执行
    <script src="js_01.js">
        // 弹窗
        alert(123)
        // 接受定义的button标签
        var btn = document.getElementsByTagName('button')[0]
        //在控制台打印button
            console.log(btn);
    </script>
</body>

</html>
```

### 二、JS获取标签

#### 2.1独有标签的获取

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>标题</title>

</head>

<body>
    <button>按钮</button>
    <script >
        // console.log();——表示在控制台输出，相当于print，
        //title就是文档的标题，
        console.log(document.title)
        //head就是文档的头部
        console.log(document.head)
        //body 就是文档的body
        console.log(document.body)
    </script>
</body>

</html>
```

#### 2.2其他特有标签的获取

```html
    <script >
        //JS变量不区分大小写，通过var定义
        //通过id获取单个元素，document表示当前文档，
        var p1 = document.getElementById("p1")
        console.log(p1);
        var sp1 = document.getElementsByClassName("sp1")[0]
        //获取到的是一个集合，是一个列表形式，多个元素，通过下标来指示要获取哪个
        console.log(sp1);
        //同理，
    </script>
```

#### 2.3修改元素的内容

```html
    <script >
        var p1 = document.getElementById("p1")
        console.log(p1);
        //修改文本的内容
        p1.innerText="今天是个好天气"
        //修改文本的内容，但是也可以修改文本标签
        p1.innerHTML="<h1>今天是个好天气</h1>"
        console.log(p1);
        //innerText，innerHTML获取到的元素为多个时，不能修改多个，只能修改一个
    </script>
```

#### 2.4通过js标签获取元素

```html
<body>
    <button>按钮</button>
    <p id="p1" name="pp">一个</p>
    <p name="pp">两个</p>
    <span class="sp1">我是文本标签</span>
    <span class="sp1">我是文本标签</span>
    <script >
        //通过标签来获取元素也是多个，不存在单个的现象
        var p1 = document.getElementsByTagName("p")[0]
        console.log(p1);
        //通过name属性来获取元素
        document.getElementsByName('pp')[0]

        //通过css选择器来获取元素,通过id来获取则只有一个，只获取第一个元素，不管有多少元素。
        document.querySelector('#p1')
        //获取到所有的元素，并通过下标来取直
        document.querySelectorAll('.sp1')[0]
    </script>
</body>
```

### 三、JS简单事件

```html
<body>
    <button>按钮</button>
    <button>按钮</button>
    <button>按钮</button>
    <div id="box"></div>
    <script>
        //通过标签名获取第一个按钮
        var btn = document.getElementsByTagName("button")
        //绑定事件，每点击一次就在控制台上打印出一个1
        //单击事件
        btn[0].onclick=function(){
            //在事件当中this就表示接受事件的元素
            console.log(1);
            console.log(this);
        }
        //双击事件
        btn[1].ondblclick=function(){
            console.log(1);
        }

        //划入事件
        var box = document.getElementById("box")
        box.onmouseenter=function(){
            console.log(1);
        }
        //划出事件
        box.onmouseleave=function(){
            console.log(2);
        }
    </script>

</body>
```

### 四、JS修改样式

```html
<body>
    <div id="box"></div>
    <script>
        var box = document.getElementById("box")
        box.onclick=function(){
            //第一种修改样式的方式的方式，将盒子变大
            // box.style.width="300px"
            // box.style.height="300px"
            // 第二种修改样式的方式，下面的方法更好一点
            box.style["height"]="300px"
            box.style["width"]="300px"
            //第三种修改样式的方式
            box.style.cssText="width:300px"
        }
    </script>
</body>

<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>标题</title>
    <style>
        div{
            width: 100px;
            height: 100px;
            background-color: red;
        }
        .div1{
            width: 300px;
            height: 300px;
            background-color: orange;
        }
    </style>

</head>

<body>
    <button>按钮1</button>
    <button>按钮2</button>
    <div id="box"></div>
    <script>
        var box = document.getElementById("box")
        box.onclick=function(){
            //第一种修改样式的方式的方式，将盒子变大
            // box.style.width="300px"
            // box.style.height="300px"
            // 第二种修改样式的方式，下面的方法更好一点
            box.style["height"]="300px"
            box.style["width"]="300px"
            //第三种修改样式的方式
            box.style.cssText="width:300px"
            
        }
        //第四种方式，在style写好样式，之后在代码中添加属性。
        var btn = document.getElementsByTagName('button')
        btn[0].onclick=function(){
            box.className="div1"
            //只能执行到div2，div1不能执行
            box.className="div2"
            //添加id的属性他的值为div1，无则增有则改。
            box.setAttribute("id","div1")
            //判断阿哥i属性是否存在，存在返回true，反之返回false
            box.hasAttribute('id')
            //获取该属性的属性值，
            box.getAttribute("class")
        }
        btn[1].onclick=function(){
            //删除class属性，
            box.removeAttribute("class")
        }
    </script>
</body>

</html>
```

### 五、JS的数据类型

- number：在js里面不区分整形和浮点型，类型都是number类型
- 布尔值：
- undefined：未定义，变量声明之后没有赋值
- 字符串：
- 空值：
- 对象object

```html
<script>
        var a = 1
        var b = false
        //空值
        var c
        // c,d,f都是对象类型
        var d = {"nihao":"你好"}
        var e = [1,5,6,4]
        var f = null
        console.log(typeof a);
    //结果是true，undefined是继承自true中
        console.log(null==undefined);
    </script>
```

