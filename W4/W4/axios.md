#             axios 学习

## 1 json-server 

是Node 模块，运行 Express 服务器，你可以指定一个 json 文件作为 api 的数据源。 

简单的说，它可以模拟小型后台接口，

在一个JSON文件中操作数据，是基于的node.js的一个模块



#### 数据存放格式：

文件名：db.json

```
{
  "posts":[
    {
      "id": 1,
      "titie": "高数",
      "author": "同济"
    },
    {
      "id": 2,
      "titie": "线代",
      "author": "清华"
    }
  ],
  "comments":
          [
            {
              "id": 1,
              "lan": "en",
              "postid": 1
            },
            {"id": 2,
              "lan": "ch",
              "postid": 2}
          ],
  "profile": {
    "name": "typicode"
  }

}
```



#### 启动服务：

**在db.json 目录下**：

```
json-server --watch db.json
```





## 2 axios 简介

Axios 是一个 [基于 promise 的]HTTP 客户端，

适用于 node.js 和浏览器

####                     特性  

**1在浏览器中发送 xhr请求**

 **2在nodejs中发送http请求**

**3 支持promise的API**

**4 转换 请求和响应的数据**

**5 取消请求**

**6 自动转化为json数据**

**7 保护跨站攻击**



####             引入方式



```
<script src="https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js"></script>
```







#### 使用方式

#####   1  GET请求 调用API 获取数据

```
const btn=document.querySelectorAll('.n1')
const ans=document.querySelector('.ans')
btn[0].addEventListener('click',function (){
    axios({
        method:"GET",
        url: ' http://localhost:3000/posts/1',


}).then(function (resonce){
      ans.innerHTML=resonce
        console.log(resonce)
    })
})
```

还是绑定到按钮实现**异步**

然后**创建一个axios对**象

**传参:  比如method  url等属性**

调用promise的then 方法

在服务器成功返回response 后执行**回调函数。**

从而实现AJAX操作。



##### 2 POST请求 调用API 更新增添数据库里的数据

```
btn[2].addEventListener('click',function (){
    axios({
        method:"POST",
        url: ' http://localhost:3000/posts',
        data:{
            title:"原神",
            author:"mihoyo"
        }

    }).then(function (resonce){
        ans.innerHTML=resonce
        console.log(resonce)
    })
})
```

相较于get请求 在axios参数中 多了一段要插入的数据。

同时url不传入id  而是选择插入数据的文件位置





##### 3 PUT请求 调用API 修改数据库里的数据

```
btn[1].addEventListener('click',function (){
    axios({
        method:"PUT",
        url: ' http://localhost:3000/posts/4',
        data:{
            title:"LOL",
            author:"腾讯"
        }

    }).then(function (resonce){
        ans.innerHTML=resonce
        console.log(resonce)
    })
})
```

相较于get请求 在axios参数中 多了要修改的数据内容。

**url要传入id**  表明是要修改哪个数据



##### 4 delete请求 调用API 修改数据库里的数据

```
btn[3].addEventListener('click',function (){
    axios({
        method:"delete",
        url: ' http://localhost:3000/posts/5',
      

    }).then(function (resonce){
        ans.innerHTML=resonce
        console.log(resonce)
    })
})
```

 **delete注意要小写。**







## 3 axios 常用方法实现增删改查

```
axios.request(config) // 发送请求

axios.get(url)   //发送get类请求

axios.delete(url)  //发送delete类请求

axios.post(url)  //发送post类请求

axios.put(url)  //发送put类请求

```



 



## 4 axios返回的响应结果的结构

```
Object{
config:...   //配置对象  包含了请求类型 请求url 请求体等
data:...   //响应体 是个对象（axios自动将json进行了解析）
headers： //响应头
request： //axios在发送请求时所创建的原生xhr对象
status：响应状态码
statusText：响应状态字符串
}
```







## 5 axios的请求配置

发出请求的可用配置选项

只有url是必需的  如果未指定methon  默认是GET

其他可选项：

```
axios({
baseURL:... ,            //基础url 会被添加到url里面 除非url是固定的


transformRequest：[function(data,headers){
//  表示允许在向服务器发送前，修改请求数据
return data;
}]，



transformResponse: [function (data) {
    // 对 data 进行任意转换处理（在传递给 then/catch 前）
    return data;
  }],

 headers: {'X-Requested-With': 'XMLHttpRequest'},
//设置请求头

 params: {
    ID: 12345
  },
设置请求中url所携带的参数 （设置的时候以obj形式设置）

})
```







## 6 axios的默认配置

```
axios.default.属性=值
```

例如：

```
 axios.defaults.method='GET'
    axios.defaults.baseURL='http://localhost:3000'
```

在**5** 中的所有请求配置

都可以设置默认值





## 7 axios的对象实例化

应用场景：

当某个请求在不同情况下要给不同的服务器发消息的时候 

可以实例化两个不同的axios对象

对其进行default值默认设置即可

代码：

```
const eyumbo=axios。creat({

baseURL;'https://api.openal'
timeout:2000
})
```

实例化出一个叫eyumbo的axios对象



之后的操作 和操作axios是一样的。







## 8 拦截器



分为请求拦截器和响应拦截器

### 请求拦截器：

对请求体的data做处理 并进行条件判断 

不满足条件：  **拦截此次请求的发送**





### 响应拦截器：

对响应体的data做处理 并进行条件判断 

不满足条件：  **拦截此次响应的发送**





设置方法：

```
axios.interceptors.request.use(config=>
{
    console.log("设置请求拦截器 通过")
    return config
},error=>{
    console.log("设置请求拦截器 拦截")
    return Promise.reject(error)
})
// 设置请求拦截器


axios.interceptors.response.use(config=>{
    console.log("设置回应拦截器 通过")
},error=>
{
    console.log("设置回应拦截器 拦截")
    return Promise.reject(error)
})
```

**在请求拦截器中 可以用config.属性 的方式 对请求参数进行设置**

**实质上还是对promise对象的then方法的继承和封装**



当有多个request拦截器和response拦截器的时候



request拦截器：先执行位于代码最下端的



response拦截器： 最后执行位于代码最下端的









## 9 请求取消 （短时多个相同请求实现防抖）





```
let cancel=null  //先设置为空
btn[0].addEventListener('click', function () {
if(cancel!==null)
{  //判断 上一个请求是否结束 如果不结束  就调用cancel函数 将上个请求取消
    cancel()
}

    axios({

        url: '/posts',
      cancelToken:new axios.CancelToken(c=>{
          cancel=c
      }
      //创建一个新的axios并将取消方法给该函数内部的axios
      )

    }).then(function (resonce) {
        ans.innerHTML = resonce
        console.log(resonce)
        cancel=null
        //要注意此时如果请求返回成功 该请求结束 要把cancel再设为空。
    })
})

```



cancel在不为空的时候实质上就是一个和当前axios绑定的取消函数

取消时候直接调用：



```
cancel()
```











## 10           axios源码分析

**手写模拟实现axios工作原理：**



```
function Axios(config) {
    this.config = config;
}

function dispatchRequest(config) {
    console.log("调用该函数")
    return xhrAdapter(config).then(response => {
        console.log(JSON.parse(response.data))
        //对响应结果转换处理。
        return response
        // 返回结果
    }, err => {
throw err
    })
}

function xhrAdapter(config) {
    console.log('调用xhrAdapter')
    return new Promise((resolve, reject) => {
        //在内部发送AJAX请求
        let xhr = new XMLHttpRequest()
        //xhr 实质上发送的请求
        xhr.open(config.method, config.url)

        xhr.send()
        //发送

        xhr.addEventListener('readystatechange', function () {
            if (xhr.readyState === 4) {
                if (xhr.status >= 200 && xhr.status < 300)
                {
                    resolve(
                        {
                            config:config,
                            data:xhr.response,
                            headers:xhr.getAllResponseHeaders(),
                            request:xhr,
                            status:xhr.status,
                            statusText:xhr.statusText


                        }
                    )
                }
                else
                {
                    reject(new Error('请求失败！！！！！'))
                }
            }
        })
        //判断服务器是否反映成功 如果成功 调用resolve 一直回调


    })
}

Axios.prototype.request = config => {
    //发送请求 创建promise对象
    let promise = Promise.resolve(config)
    console.log(promise)

    let chains = [dispatchRequest, undefined]
    //  声明一个长度为2 的数组  用来承接promise的then方法的两个回调。
    // undefined用来占位

    let res = promise.then(chains[0], chains[1])
    console.log(res)
    //then 制定回调 最后res还是一个"fulfilled"的promise
    return res

}

let axios = Axios.prototype.request.bind(null)

axios({
    method: 'GET',
    url:'http://localhost:3000/posts'
}).then(response=>{
    console.log(response)

},err=>{

})
```



#### 10.1 axios和Axios的差异

从语法上来说axios不是Axios的事例

但是从功能上来说，axios是Axios的实例

（axios是Axios.protopype.request.bind()这个函数执行后返回的函数）

它具有Axios原型对象上所有的方法和属性



#### 10.2 axios instance和别名的辨析：

axios和其他别名 都是一个能发送各种请求的函数 **用法是相同的**

**至是默认配置不一样**

instance没有axios后的create CancelToken等方法







#### 10.3   axios执行过程 



request(config)   ==》  dispatchRequest(config) ==》xhrAdapter(condig)



#### 10.4 cancel取消请求的具体原理



当配置了cancelToken对象的时候 先保存cancel函数

**具体创建**：

1 创建一个用于将来中断请求的cancelPromise

2 定义一个用于取消的cancel函数

3 将cancel参数传递开放出来



**调用取消**：

1 执行cancel函数 传入错误信息message

2 此时cancelPromise变为成功

3 canclePromise的成功回调 执行AJEX的abort函数 实现 取消