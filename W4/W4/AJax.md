#                                        AJAX学习

## 1 AJAX 简介

**Ajax全称为Asynchronous Javascript And XML，即异步JS和XML**

最大的优势：**无刷新获取数据**



优点：

可以无刷新页面与服务端进行通信
允许你根据用户事件来更新部分页面内容



缺点：

1. 没有浏览历史，不能回退
2. 存在跨域问题（同源）
3. SEO不友好（爬虫获取不到信息）





## 2 XMl标记语言

使用途径：用来传输和存储数据

和html十分相似

HTML中都是预定义标签 而XMl全部都是自定义标签

目前已经被JSON取代







## 3 HTTP协议的请求报文和响应报文的文本结构



都分为 行 头 空行 体 四部分

#### 请求报文：

```
···
行: 请求类型（GET？POST？）  url     HTTP协议版本
头： 有关该请求的各种属性 以键值对的方式存储
空行：
体：向服务器发送的各种参数（get 请求体为空，post请求 请求体中可以带参数）
···
```



#### 响应报文：

```
···
行 HTTP协议的版本 状态码  响应状态字符串
头：有关该响应报文的各种属性 以键值对的方式存储
空行：
体：服务器返回的内容 比如一段HTML语言构成的字符串等
```







## 4 NodeJS与Express框架

*Node.js 就是运行在服务端的 JavaScript*

而Express 是**一个简洁而灵活的 node.js Web应用框架,** 

提供了一系列强大特性帮助你创建各种 Web 应用，和丰富的 HTTP 工具。

- 定义了路由表用于执行不同的 HTTP 请求动作。



Express 应用使用回调函数的参数： **request** 和 **response** 对象来处理请求和响应的数据。

**以get为例：**

```
app.get('/', function (req, res) {
   // --
})

```

设置了服务器在**get请求 时候的路由**







## 5 AJAX基本操作（以点击按钮发送请求 实现div内部文本更改）



#### 服务器设置：

```
//引入express框架
const  express=require("express")


//创建应用对象
const app=express()


//创建路由规则
//request 是对请求报文的封装 response是对响应报文的封装。
app.get('/server',(request,response)=>{
    response.setHeader('Access-Control-Allow-Origin','*')
    response.send('hello world!')
 
})
//response.setHeader('Access-Control-Allow-Origin','*')  更改回应报文头 使其允许跨域


//监听端口启动服务
app.listen(8000,()=>
{
    console.log("服务器已经启动，正在监听8000端口中。。。")
})

//

```





#### 客户端设置

```
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport"
          content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .rescult {
            background-color: pink;
            width: 200px;
            height: 100px;
            border: solid 2px black;
        }
    </style>
</head>



<body>
<button>点击发送请求</button>
<div class="rescult"></div>
</body>

<script>
    const btn = document.querySelector('button')
    btn.addEventListener('click', function () {
        const xhr = new XMLHttpRequest()
        //创建AJAX请求对象
        xhr.open('GET', 'http://127.0.0.1:8000/server')
        //对象初始化 设置请求方法和url
        xhr.send()
        //发送
        xhr.addEventListener('readystatechange',function () {
//if判断服务器是否返回了所有结果（readyState为4的时候返回了所有结果）
            if (xhr.readyState === 4) {
                //判断响应状态码是否是200到300（此时才是成功响应）
                if (xhr.status >= 200 && xhr.status < 300) {
                    console.log(xhr.status)
                    console.log(xhr.statusText)
                    console.log(xhr.getAllResponseHeaders())
                    console.log(xhr.response)
                    /* xhr 有四个常用的属性



                     */
                    document.querySelector('.rescult').innerHTML = xhr.response
                }
            }
        })
    })
</script>
</html>
```

#### 知识点总结：

1 **xhr是XMLHttpRequest 的实例化对象**  具有以下方法：

```
  xhr.open('GET', 'http://localhost:8000/server')
```

**open 方法** 设置请求类型和请求发送的URL

```
xhr.send()
```

**send方法** 发送请求包





**2 xhr具有readystatechange** 事件  该事件可以调用事件监听器

readstatechange 是xhr中的请求内容发生变化的时候 调用的事件

**要使用if判断！！！**



**3 xhr的常用的属性：**

xhr.readyState  属于num型  当为4 的时候 表明服务器已经将响应包完全发回来。

xhr.status  响应状态码 当200-300之间 表明响应成功

xhr.getAllResponseHeaders() 该方法发挥所有的响应包头 以键值对的方式。

xhr.response 响应体：一般是返回后浏览器要加载的数据包







## 6 AJAX设置URL的参数

途径：更改open方法：

```
xhr.open('GET', 'http://localhost:8000/server?key1=value1&key2=value2&...')
```

**即在URL后先‘？’ 后直接缀参数**。

```
？key1=value1&key2=value2&...
```

以**键值对**的形式





## 7 AJAX设置POST请求：

#### 分别修改客户端和服务器

服务器：

```
app.get('/server',(request,response)=>{
  函数体
 
})
```

改为：

```
app.post('/server',(request,response)=>{
  函数体
 
})
```

即可





客户端修改open方法第一个参数

```
 xhr.open('POST', 'http://localhost:8000/server')
```





#### post请求设置请求体

```
xhr.send("key1=value1&key2=value2....")
```

**可以发送任意格式的数据 只要服务器可以解析即可**





#### post请求设置请求头

```
xhr.setRequestHeader("Content-type","application....")
```

设置系统预定义的 请求头键值对





```
xhr.setRequestHeader("diy-name","eyumbo")
```

在发送请求的时候会报错 因为“diy-name”不是系统预定义的键



解决方法：

第一步 ：在服务器端设置

```
response.setHeader('Access-Control-Allow—Headers','*');
```

即设置**允许发送所有的请求头**



第二步：

```
app.post('/server',(request,response)=>{
  函数体
 
})
```

中post 改为all  即可以接收所有类型的请求



```
app.all('/server',(request,response)=>{
  函数体
 
})
```







## 8 IE浏览器缓存问题

ie浏览器存在问题：在短时间内接收到两个相同的请求时 

会把第一次请求的结果缓存在浏览器内

**在第二次请求时直接调用第一次结果 而不接受服务器新的回应**



解决方法：

```
  xhr.open('POST', 'http://localhost:8000/server?t='+Date.now()')
```

即每次请求都传入一个data.now的时间戳

这样每次请求都不相同  所以在ie上可以实时获得服务器返回的数据

```
?t='+Date.now()'
```





## 9 超时取消请求

增添设置 设置超时的时间

```
xhr.timeout=2000
```

当请求时长大于两秒的时候 **自动取消请求**。

同时还可以触发**事件 timeout**

```
 xhr.addEventListener('timeout',function (){
                    alert("请求未响应，请稍后再试！！")
                })
```





**事件error**

```
 xhr.addEventListener('error',function (){
                    alert("网络未连接！！")
                })
```

该事件应用于 **断网的时候 即请求包发不出去**







## 10 请求包的手动取消

**调用abort函数** 

手动取消请求包

可以绑定到按钮上

```
btn.addEventListener('click',function (){
                    xhr.abort();
                })
```





## **11 处理短时间内多个相同请求**

思路 ：添加一个布尔值的flag初始值为0    

   当生成请求的 时候

每次先判断flag==1？

**若为1** 则调用abort方法取消上次的请求

再生成一个新的请求（类似js中的防抖） 同时flag=1



**若为0** 说明之前没有未响应请求  则直接生成请求  flag=1



代码实现：

```
let flag=0;
let xhr=null;
 btn.addEventListener('click', function () {
        if(flag)
        {
        xhr.abort()
        }
        xhr = new XMLHttpRequest()
        flag=1
        //创建AJAX请求对象
        xhr.open('GET', 'http://127.0.0.1:8000/server')
        //对象初始化 设置请求方法和url
        xhr.send()
        //发送
        xhr.addEventListener('readystatechange',function () {
//if判断服务器是否返回了所有结果（readyState为4的时候返回了所有结果）
            if (xhr.readyState === 4) {
                //判断响应状态码是否是200到300（此时才是成功响应）
              flag=0
               //此时要注意将flag归零
                }
            }
        })
    })
```

