# JS提升

### 一、JS的内置对象

```html
    <script>
        console.log(Math.sqrt(4));//开平方
        console.log(Math.abs(-4));//绝对值
        console.log(Math.PI);//圆周率
        console.log(Math.pow(2,3));//求二的三次方
        console.log(Math.floor(4.6));//向下取整 ，4
        console.log(Math.ceil(4.6));//向上取整 5
        console.log(Math.round(4.6));//四舍五入
        console.log(Math.max(2,3,5,6,8));//求最大值,最小值相同
        console.log(Math.random());//取0到1之间的随机数，但没有1.


        //定义时间对象
        var time = new Date()
        console.log(time.getFullYear());//获取年份
        console.log(time.getMonth()+1);//获取月份，但是默认从零开始
        console.log(time.getDate());//获取日期
        console.log(time.getHours());//获取小时
        console.log(time.getMinutes());//获取分钟
        console.log(time.getSeconds());//获取秒钟
        console.log(time.getDay());//获取星期，得到的是数字
        
        console.log(Date.now);//获取时间戳
        

    </script>
```



### 二、JS的window对象

```html
<body>
<button>按钮</button>
    <script>

        //定时器与延时器

        //延时器，以指定的时间为周期执行一次,3000是毫秒
        var time1 = setTimeout(function () {
            console.log(1);
        }, 3000)

        //定时器，以指定时间为周期循环执行
        var time2 = setInterval(function () {
            console.log(2);
        },2000)

        //清除延时器
        clearTimeout(time1)
        //清除定时器
        clearInterval(time2)

        var btn = document.getElementsByTagName("button")
        btn[0].onclick=function () {

            //原页面跳转页面
            //window.location.href="https://www.baidu.com"

            //新建页面跳转
            window.open("https://www.baidu.com")
        }
    </script>
</body>
```



### 三、JS函数

```html
    <script>


        //JS函数参数：只有形参实参不定长参数,相当于c++的函数语法
        //有名函数
        function func() {
            console.log("这是有名function函数");
            console.log(1);
        };
        //匿名函数
        document.onclick = function () {
            console.log(2);
            console.log("匿名函数");
        };
        //多余的参数是undifend
        function func1(pa, rams, y) {
            console.log(pa + rams);
            console.log(y);
            return pa + rams
            console.log(arguments);//会接受所有参数
        };
        a = func1(5, 6);
        //函数自调用,在定义函数时前面加~，后面加括号,函数自调用一定要加分号表示结束
        ~function () {
            console.log(5);
        }();

        //函数作用域
        var b = 5;//函数外用var定义的是全局变量，作用在全局
        function f() {
            var a = 200 //函数里用var定义的是局部变量，作用在局部
            b = 200 //此时b改成了全局变量
        }
        f()
        console.log(a);//a is not defined
        console.log(b);//b is 5


        var a = 5
        function f() {
            var a = 100
            function f1() {
                var a = 300
            }
            f1()
            console.log(a);
        }

        console.log(a);  //5
        f() //100
        console.log(a);//5
        //块级作用域
        {
            var a = 10
        }
        alert(a) //5
        {
            let x = 6 //用let定义的变量作用于只能是块级作用域
        }
        alert(x)//会报错
        //递归调用
        function ff(x) {
            if (x==1) {
                return 1
            }
            return x+ff(x-1)
        }

    </script>
```



### 四、JS异常

```html
    <script>
        //函数异常

        function ff() {
            try {
                console.log(a);
            } catch (e) {
                alert("错误类型：" + e.name + "错误消息" + e.message)
            } finally {
                alert("代码执行完毕")
            }
        }
        ff()

        //自定义异常
        function getSum(a) {
            try {
                if (a > 200) {
                    throw "数字太大了"
                }
                if (a < 200) {
                    throw "数字太小了"
                }
            }catch (e) {
                alert(e)
            } finally {
                alert("代码执行完毕")
            }

        }
        getSum(3)
    </script>
```

**BootstrapCDN:前端开发的框架**