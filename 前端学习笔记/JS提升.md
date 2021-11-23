# JS提升

### 一、JS操作符

- 算术运算符，赋值运算符，逻辑运算符，比较运算符

```html
    <script>
        var a =1
        var b =2
        var c = '3'
        //算术运算符+ - * /,在js里面，数字和字符串相加起到了拼接的作用
        document.write(a+c+'<br>')
        //存在隐式转换，结果是2，但是+只是拼接，其他的算数运算符有隐式转换
        document.write(c-a)
        //true是1，结果是2
        document.write(a+true)
        //赋值运算符,里面的赋值运算符，前自增和后自增相当于c++里的
        document.write(b+=1)
        document.write(b++)
        document.write(++b)

        //比较运算符，逻辑运算符
        //== 表示的是相等，先转换类型，再去比较它们的类型 ！=不等
        //=== 全等，只有类型和数值一样才会返回真、！==不全等
        var num1=2
        var num2='2'
        console.log(num1==num2);//结果是真，
        console.log(num1!=num2);//结果是假，
        console.log(num1===num2);//假
        console.log(num1!==num2);//真

        //与或非——&& || ！，与c++是一样的结果。
    </script>
```



### 二、JS流程控制

```html
<script>
        //条件分支,使用和c++的语法是一样的
        var a = 2
        if (a == 2) {
            console.log(111);
        } else if (a == 1) {
            document.write('今天不起床')
            console.log(222);
            document.write('今天有作业')
        } else {
            console.log(333);
            document.write('今天没有作业')
        }
        var b=1
        switch (b) {
            case 1:
                document.write('今天是星期一')
                break;
            case 2:
                document.write('今天是星期二')
            default:
                document.write('今天啥也不是')
                break;
        }
</script>
```



### 三、JS循环

```html
    <script>
        //循环,同c++一样
        for (let index = 0; index < 10; index++) {
            document.write("第几分钟"+index)
        }
        //先判断在执行
        while (b++) {
            document.write('这是while循环')
            if (b>=5) {
                break
            }
        }
        //先执行，后判断
        do {
            document.write('这是while循环')
            if (b>=5) {
                break
            }
        } while (b++);


        //for in循环
        var arr = [1,2,3,4]//这是数组
        var arry = {"name":"北斗","age":"18"}
        for (var i in arr) {
            document.write(i)
        }
        for (var i in arry) {
            document.write(i)
        }

    </script>
```



### 四、JS字符串方法

```html
    <script>
        var st = 'hello word'
        console.log(st.length);//获取字符串的长度
        console.log(st.indexOf("e"));//获取特定字符串的下标
        console.log(st.charAt(2));//根据下标，获取字符串的值
        console.log(st.split(" "));//切割字符串，得到数组类型
        console.log(st.replace("h","H"));//替换字符串中的字符，只能替换一个
        console.log(st.slice(0,5));//根据下标切片，左闭右开的，可以是复数，但不能倒着切
        console.log(st.substring(5,0));//根据下标截取，左闭右开的，不可以是复数，但能倒着取
        console.log(st.substr(1,4));//从下标1开始，截取4个长度，左闭右开的，不可以是复数，但能倒着取
    </script>
```



### 五、数组方法

```html
 <script>
        var arr = ["草每","西瓜",'香蕉',"哈密瓜"]
        console.log(arr.length);//数组长度
        console.log(arr.indexOf("西瓜"));//获取西瓜下标
        console.log(arr.push("桃子"));//在尾部添加数组元素，返回数组长度
        console.log(arr.unshift("三个"));//在头部添加数组元素，返回数组长度
       console.log(arr.splice(2,1));//从第二个开始删除一个 
        console.log(arr.pop());//不传的话默认删除最后一个，返回被删除的元素
        console.log(arr.slice(1,3));//数组切片  都是下标，遵循左闭右开的原则
        console.log(arr.join("12"));//数组拼接
        var arr2 = [9,5,7,8]
        console.log(arr2.sort());//排序
        console.log(arr2.reverse());//反转
      
    </script>
```

