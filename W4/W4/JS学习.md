

# JS学习

### 1 js简介

运行在浏览器上的编程语言

实现：

网页特效 表单验证 前后端数据交互  服务端编程

![](img/Snipaste_2023-09-05_12-49-33.png)





### 2 js书写位置：

行内 内部 外部

**内部**：

在body内书写

写在body的最下方内



**外部：**

 写在  .js 文件中

引用：

```
<script src="XXX.js">

</script>
```

**内部和外部不能混着用**





### 3 JS语法和常用函数

##### 3.1 注释和结束符

```
//  单行注释

/* 
      多行注释
*/
```

结束符是 ;  但是可以不写



##### 3.2 输入和输出

```
1  document.write("")

   引号内容里面可以直接写标签（使用html语言）


2 alert("")
   弹出警告提示框
   
3 console.log(" ")
控制台打印



输入：
prompt("你是gg还是mm？？")
```



##### 3.3 执行顺序

自上而下依次执行渲染

**但是alert和prompt会被先执行**



##### 3.4 变量

```
let 变量名


js是大小写敏感的语言
```



##### 3.5 数组

```
let arr=[10,20,30]
  索引 从0开始
  
let arr= new Array(1,2,3)



修改：
arr[1]=300

增加：
arr.push(5,11)
添加到数组末尾  该方法返回值为 新数组的length

arr.unshift(8,"nihao")
添加到数组开头 该方法返回值为 新数组的length

遍历：
for(i=0;i<arr.length;i++)
{
  循环体
}

删除：
arr.pop()
从队列末尾弹出一个元素并返回

arr.shift()
从arr头部弹出一个元素并返回


arr.splice(起始索引，删除的元素数量)
2个参数  索引从0开始
```





##### 3.6 常量

```
const G=9.8
```





##### 3.7 数据类型

```
类python 弱数据类型

NaN：计算错误
NaN是粘性的 任何对NaN的操作都会返回NaN


外双内单，或者外单内双
必要时可以使用转义符\ 

字符串拼接：  str1 + str2  (字符串也来可以和数字型一起拼接)
```





#####  3.8 模版字符串

```
document.write(`我今年${age}岁了`)


 ${}内写变量    使用斜括号  ` `
```





##### 3.9 typeof()

```
let num="你好“
console.log(typeof(num))
```





##### 3.10 类型转换函数

```
newstr=Number(str);

newstr=  parseInt(str)  只保留整数部分 

newstr=  parseFloat(str)
```



##### 3.11 运算符号

```
==  左右的值是否相等
===  左右的类型和值是否都相等
!==  左右两边是否不全等


 console.log(2=="2")    ture
  console.log(2==="2")  false
  console.log(2!=="2")  ture
```



##### 3.12 选择和循环



C-like  和c一样





### 4 函数操作



##### 4.1 封装

```
function 函数名()
{

}
```



##### 4.2 变量名重复

优先调用函数内的那个变量

逐层查找



##### 4.3 匿名函数

```
function()
{

}
```

常用操作：

1 函数表达式

```
let fn=function()
{

}
```

相当于一种 特殊的类



2 立即执行函数

```
  (
        function (a, b) {
            console.log(a + b)

        }
        (2, 100)
    )
```

匿名函数第最外层括号后面一定要  **加分号**

在括号内先声明再调用



3 逻辑中断

利用&&和||实现（c-like）



```
&& 左边false  右侧代码不再执行。

||  左边true 右侧代码不再执行。

 console.log(11||22)  //两侧都ture 返回左侧
 console.log(11&&22)   //两侧都true 返回右侧
```

从而为函数添加默认值

 例：

```
 function  sumage(fage,mage)
    {
        let  f=fage||27
        let m=mage||25
        return f+m


    }
    let fage=Number(prompt("父亲年龄？" ))
    let mage=Number(prompt("母亲年龄？"))
    let ans=sumage(fage,mage)
    document.writeln(`年龄之和为${ans}`)

```



**4.4 Boolean型转换**

```
let newboolean= Boolean(NaN)
```



''、0、undefined、null、false、NaN 都是false

''和null数字转化后是0

undefined数字转换后是  NaN



### 5 对象

##### 5.1 基本操作

```
声明：
let obj={
h:500,
w:500,
name='123'

}

增改 直接进行
原来有就是 修改操作
原来没有 就是增添操作


删除：
delete obj.name

查询：
console.log("obj.name")
或者
console.log("obj['name']")
```



##### 5.2 声明方法

```
let obj=
{
act1:
      function()
      {
      函数体
      }
}
```



##### 5.3 对象内部的遍历

```
类py、
for(let k in obj)
{
循环体
}



```

例子：

```
 let obj={

      name:"123",
      hi:2,
      w:300,
      say:
      function ()
      {
          for (let it in obj)
          {
              console.log(`这是${obj[it]}`)
          }
      }
  }
```

可以对象内部 **for in 对象本身**





### 6  内置对象 js包

####    6.1 math包

```
 ma=Math.random()    /* 生成0 到1 的随机数 包括0 不包括1*/
 ma=Math.ceil(ma)    /* 向上去整*/
 ma=Math.floor(ma)   /* 向下去整*/
 ma=Math.max(1,23)   /* 求最大值 可以调用数组*/ 
 ma=Math.pow(2,10)   /* 幂运算  2的十次方*/ 
 ma=Math.abs(-100)   /* 绝对值*/
```



取随机数

```
    ma=Math.floor(Math.random()*1024)
    /* 取0到1024 之间的随机整数  不包括1024  */
    
    
    ma=Math.floor(Math.random()*512+512)
      /* 取512到1024 之间的随机整数  不包括1024 */
```



### 7 JS  API

##### 7.1 let和const的选择

开发中一般先使用const

 遇到需要更改的变量再修改声明为let

```
const arr=['123','147']

const obj={
age:18,
gender:'man'
}
```

数组和对象obj' 使用const声明

可以修改内部的内容。





##### 7.2 DOM常用方法

###### 7.2.1  document.querySelector( )

```
 const boxhd=document.querySelector('.box-hd')
  
 //  获取 匹配到的标签选择器所对应的第一个标签
 
 参数：CSS选择器字符串  返回值：css选择器所匹配的第一个元素对象
```





###### 7.2.2 **document**.querySelectorAll()

 参数：CSS选择器字符串  

返回值：css选择器所匹配的所有元素对象组成的 NodeList

 `NodeList` **不是一个数组**，是一个类似数组的对象 (*Like Array Object*)。

**可以使用索引号 但是没有pop和push等方法**



###### 7.2.3   对象.innerText

innerText 就是所设置的box中的文字内容

```
 const box1=document.querySelector('.one')
 console.log(box1.innerText) //输出文字内容
 box1.innerText="hello world"  //修改文字内容
 console.log(box1.innerText)
```

只修改文字  不解析标签



###### 7.2.4 对象.innerHTML

可以解析标签

```
  box1.innerHTML = '<h3>你好 世界 </h3>'
```



##### 7.3  选取对象的css样式更改

方法一：通过.style.css属性来更改

```
 box.style.backgroundColor='pink'
 box.style.height='50px'

```

方法二：先在css中预载样式设置

在script执行的时候  进行判断 条件满足就修改  对象.className 从而实现渲染

例如：

```
 <style
        .tibu
        {
            background-color: steelblue;
            height: 50px;
            line-height: 50px;
        }
  </style>
  
  
  
  <script>
  if (people[ans]==='jack')
    {
        w3.className='tibu'
    }
  </script>
```



方法三 ：classList方法实现 类名的添加  **(同时不覆盖之前的类名)**

例如：

```
 w3.className='ti'
    if (people[ans]==='jack')
    {
        w3.classList.add('tibu')
    }
```

classList的常用方法：

```
box.classList.add('tibu')  添加类名
box.classList.remove('ti')  删除类名
box.classList.toggle('ti')  list中有ti 删去 ，没有ti则加上
```







##### 7.4   操作表单元素

获取表单元素值

```
const pass=document.querySelector('div input') console.log(pass.value)
```





##### 7.5 自定义属性

![image-20230912195936255](img\image-20230912195936255.png)

自定义

```
<div class="make" data-id="不知道">
```



调用：

```
 const itt=document.querySelector('.make')
 console.log(itt.dataset.id)
```

**itt.dataset.id**







##### 7.6 定时器-间歇函数

实现代码的重复执行

常用方法

###### 7.6.1 打开定时器

```
let 变量名 = setInterval(执行函数,间隔时间 单位：ms)
```

函数后面不用跟括号带参数





###### 7.6.2 关闭定时器

```
clearInterval(变量名)
```



### 8 伪类选择器 :nth-child()

![image-20230912193414302](img\image-20230912193414302.png)





### 9 事件监听器

##### 9.1 语法

```
元素对象.addEventListenner('事件类型',执行函数)
```



##### **9.2 事件类型**

**mouse类：**

```
btn.addEventListener('click',down)
//鼠标点击
btn.addEventListener('mouseenter',begin)
//鼠标经过
btn.addEventListener('mouseleave',begin)
// 鼠标离开
```



**表单光标类**

```
focusing.addEventListener('focus',begin)
//表单获得光标

focusing.addEventListener('blur',begin)
//表单失去光标
```





**键盘类**

```
keyboard.addEventListener('Keydown',begin)
// 键盘按下触发

keyboard.addEventListener('Keyup',begin)
// 键盘抬起触发
```





**文本输入类**



```
textArea.addEventListener('input',begin)
// 用户输入 触发

```



### 10 事件对象

##### 10.1调用方法：

在function里面 声明

一般将事件对象声明为e或者evt

```
input.addEventListener("input",function (e){
    len=input.value.length
    ale.innerHTML=`您一共输入了${len}/20字`
    if(len>20)
    {
        ale.innerHTML=`超出字数限制`
    }
    console.log(e)
})
```





##### 10.2 常见属性

```
console.log(e.type)
//事件的类型 例如是点击click还是input输入

console.log(e.clientX)
// 这个事件发生时在页面的X坐标

console.log(e.offsetX)
//事件发生点在当前dom元素内部的X坐标

console.log(e.key)
//这个事件发生的所带按下的键盘的值  适用于 键盘类
```









### 11 trim函数 的字符串处理

**trim()函数**

**删除字符串两侧的空格**





### 12 环境对象 this

**谁调用 this就指向谁**





### 13 事件流

##### 13.1 定义 

事件流指的是事件完整执行过程中的流动路径

事件捕获 从大到小  从父到子

事件冒泡 从小到大 从子到父





##### 13.2 捕获使用方法

```
DOM.addEventListener('click',function (){},true)

```

第三个参数 默认false 代表事件冒泡  传入true 则实现事件捕获。



**捕获相当于 父、子元素绑定的监听器在执行的时候从大到小执行**

**冒泡相当于 父、子元素绑定的监听器在执行的时候从小到大执行**





##### **13.3  阻止冒泡**和捕获

先拿到事件对象

```
事件对象.stopPropagation()
```

例子：

```
boxsmall.addEventListener('click',function(e))
{
e.stopPropagation()
}
```





##### **13.4 事件解绑**

```
ball.removeEventListener('click',fn)
```

第二个参数是函数名称

因此匿名函数作为addEventListenner的时候 无法进行事件解绑。





### 14 事件委托

利用事件流的特性

将监听器绑定在父元素上 减少注册次数 提高效率

**如何定位 事件是发生在哪个子元素上？、**



**查询事件 e里面的target元素**

**对target元素进行操作**

**同时利用target里面的tagName属性进行if判断**

```
if(父元素.target.tagName==='LI')
{
执行代码
}
```

可以精准界定哪些子元素会发生事件响应。





### 15 阻止默认行为

 **语法 **

**e.preventDefault()**



阻止某些元素的 常规默认行为。





### 16 其他事件



##### 16.1 页面加载事件

等待页面所有对象都加载完后再执行的事件



```
windo.addEventLinster('load',function(e){

需要执行的代码块

})
```







等待初始的HTML文档被完全加载后执行的事件

属于document的属性

语法：

```
document.addEventListener('DOMContentLoaded',function(){

})
```

不需要等待样式表和图片加载完毕





##### **16.2 元素滚动事件**

页面滚动的时候触发的事件

一般给document或者window添加

语法：

```
window.addEventListener('scroll',function (){
    
})
```



scrollTop和scrolLeft属性

**是可读写的 默认单位是px像素， 读写的时候不带单位**

返回被卷向上和向左的距离。

利用  if 语句进行操作

例如：

```
window.addEventListener("scroll",function (){

    if(document.documentElement.scrollTop>=500)
    
        console.log("nononononon")
        
})

```



##### 16.3 页面尺寸事件

窗口尺寸页面发生变化的事件

语法：

```
window.addEventListener('resize', function () {
    console.log("hello")
})
```



clientWidth 和clientHeight 

获取元素的可见部分的宽和高

（不包含边框，margin和滚动条等）



offsetWIdth 和offsetHeight

 包含元素自身设置的宽高，padding和border

获取出来的是数值 方便计算



offsetLeft和offsetTop

获取元素距离自己 的**带有相对定位 的更高级元素**的左、上距离





### 17 日期对象

创建

```
const  date=new Date() //当前时间


const dateFinal=new date('2023-10-1 08:00:00')
//指定时间
```



对象常用方法：

```
const year=dateFinal.getFullYear()
//获取四位数年份
const month=dateFinal.getMonth()
//获取月份 
注意取值是0-11  要+1
const dayInMonth=dateFinal.getDate()
//获取日期 今天是几号
const day=dateFinal.getDay()
//获取今天是周几
注意取值是0-6  要+1



还有.getHours() .getMinutes() .getSeconds()等常用方法。



const time=date.toLocaleString()
//获取格式化的年月日
```



时间戳：

应用：倒计时效果

倒计时=截止日的时间戳 -现在的时间戳  单位：毫秒

在转化为年月日时分秒的形式即可

调用：

```
Date.now('2023-10-1 10:00:00')
```

免去实例化的麻烦





### 18 dom节点操作

dom树中每个内容都称之为节点

分为三类  **元素节点 属性节点  和  文本节点**

元素节点就是指标签   属性节点指属性 键值对

文本节点指所有的文本

增删改查

##### 18.1 查找节点

```
查找父元素：
子元素.parentNode
//返回最近一级的父节点 找不到返回null


查找子元素

父元素.childen
//返回所有最近一级的子节点的伪数组

查找兄弟节点
元素.nextElementSibling
// 下一个兄弟节点

元素。previousElementSibling
// 上一个兄弟节点
```



##### 18.2 增加节点

两步走

**第一步创建新节点**

```
document.createElement('标签名')
//创建空的新节点

元素.cloneNode(true)
//克隆节点  包含后代节点

元素.cloneNode(false)
//克隆节点  不包含后代节点
```

**第二步将节点插入到父元素中**

```
父元素.appendChild()
//插入父元素的尾部

父元素.insertBefore(要插入的元素,在哪个兄弟元素前面)
//插入指定位置

```







##### 18.3  删除节点

```
父元素.removeChild(要删除的元素 )
```









### 19 M端事件

```
element.addEventListener('touchstart',function (){
    
})
//手指触碰到标签

element.addEventListener('touchmove',function (){

})

//手指从标签上滑动

element.addEventListener('touchend',function (){

})

//手指从元素上移开时触发
```





### 20 清空表单的方法

```
const info=document.querySelector('.info')

info.reset()


info是表单
```



### 21   window对象

bom指整个浏览器模型

bom里面包含着dom

window对象是一个全局对象 js中顶级对象

var声明的变量和函数都会变成window对象 的属性和方法





### 22  定时器 延时函数（ 执行一次）

语法：

```
let timer= setTimeOut(function(){

},等待的毫秒数)
// 设置延时函数

clearTimeOut(timer)
//清除延时函数

```



###### js执行机制：单线程





### **23 Location对象**



##### **23.1 href属性更改实现 页面的跳转**

```
执行代码：
Location.href='www.baidu.com'

//将页面跳转到百度 该语句常用在判断中 满足某个条件后实现页面跳转
```



##### 23.2 search 属性 保存的是获取地址中的参数 符号？后的部分

```
console.log(location.search)


//例如在有道上搜 hello world
https://youdao.com/result?word=hello%20world&lang=en

location.search就是“?word=hello%20world&lang=en”

```





**23.3 hash属性 获取的是地址中的哈希值 符号#后的部分**

```
例如：
https://music.163.com/#/my/
```

vue路由 用于不刷新页面 就能显示页面不同区域





##### 23.4 reload方法

```
relode方法用来刷新页面

Location.reloda()
或者
Location.reloda(true)  //加true表示强制刷新
```





### 24 navigater对象  领航员

##### 24.1  userAgent属性

**显示是PC还是安卓苹果端**



**使用if判断 是手机端就跳转到手机端网站**





### 25 history元素

 常用go方法控制前进后退

history.go(n)   前进n步  负数为-n

相当于浏览器左上角的前进后退符

代码：

```
const forward=document.querySelector('.forward')
const back=document.querySelector('.back')

forward.addEventListener('click',function (){
    history.go(1)
})

back.addEventListener('click',function (){
    history.go(-1)
})
```





### 26 本地存储

**两个对象：localStorage和sessionStorage**



localStorage **永久存储**在本地电脑 

**可以在相同的浏览器多窗口共享**



sessionStorage

**生命周期是关闭浏览器窗口**



二者数据都以键值对形式存储，且只能以字符串的形式存储



##### 简单数据类型增删改查

```
localStorage.setItem("age",'18')
//原来没有就增加 有就修改

localStorage.removeItem('age')
//删除

localStorage.getItem('age')
//查找
```

因为只能以字符串的形式存储  所以无法直接存复杂数据类型



##### 转json格式存储复杂数据类型

**转 json函数     JSON.stringfy(obj)**

**json转js对象函数 JSON.parse(json格式的str字符串)**

```

const obj={
    name:'leebo',
    age:'19'
}


localStorage.setItem('obj',JSON.stringify(obj))
//转json 存储到localStorage里面

const final_obj=JSON.parse(localStorage.getItem('obj'))
//  先从存储空间去除 再调用parse转化为js对象 

console.log(final_obj

```



### 27 字符串拼接

##### map方法

作用：遍历老数组，经过处理并返回一个新的数组

操作：

```
let arr=['小米','小华','吴京']


newarr=arr.map(function (element,index)
{
    return element+"同学"

})

console.log(newarr)



//结果：构造了一个新数组：(3) ['小米同学', '小华同学', '吴京同学']


```

##### join方法 数组转字符串

```
console.log(newarr)

console.log(newarr.join('和'))
console.log(newarr.join(''))
//中间参数就是每个元素转字符串后的分隔符  如果参数是空字符串 则没有间隔

//结果：小米同学和小华同学和吴京同学
       小米同学小华同学吴京同学
```



### 28 正则表达式

用于匹配字符串中字符组合代的模式

用来查找或者替换那些符合正则表达式的文本。实现表单验证和敏感词替换、字符串提取。



##### 声明：



```
const 变量名=/表达式/

//里面不需要加引号
```

**常用方法：**

```
reg.test(被检测的字符串)
//匹配到 返回true 否则返回false

reg.exec(被检测的字符串)

//返回一个数组，每个元素中记录着查找结果的相关信息
找不到返回null
```





##### 边界符

```
 ^和$
 ^是开始 用来匹配行首的文本
 
 $是结束 用来匹配行末的文本。
 
```

**如果^和$在一起 则表示精确匹配  即===全等**



##### 量词

用来设定某个模式出现次数

```
*    重复0次或者更多次（可有可无）
+    重复一次或更多次
?    重复0或1次
{n}  重复n次
{n,} 重复n次以上 
{n,m} 重复n次到m次、


举例应用：
^[0-9]+$ //只能是数字 但可以出现多次

^[a-zA-Z]{5,}$//只能是大小写字母 且出现五次以上
```



##### 字符类

```
[]匹配字符集合 只要和内部的任何一个匹配 就可以
[a-z] 小写字母
[a-zA-Z0-9_] 大小写字母数字和下划线

^代表取反
[^a-z]不能是小写字母，其他都可以
[^a-zA-Z0-9_] 不能是大小写字母数字和下划线

综合举例：
QQ号：
/^[1-9][0-9]{4,}$/

qq号第一位只能是1-9 不能是0 
且在第一位之后 至少要跟四个0-9 即最低是五位数
```



##### 预定义字符类

```
\d   相当于[0-9]
\w   相当于[a-zA-Z0-9_]

取反操作：

\D   相当于[^0-9]
\W   相当于[^a-zA-Z0-9_]
```





##### 修饰符

```
语法：/表达式/修饰符

/^[a-z]$/i   不区分大小写 实际效果==  /^[a-zA-Z]$/

/^[a-z]$/g   全局搜索 如果不加g只能查找到第一个满足表达式的地方

```



##### replace方法

```
字符串.replace(/正则表达式/，'替换上去的文本')


例如：

str.replace{/[a-z]/ig,"这里原来是字母"}  

效果：查找str中所有的大小写字母 将其替换成"这里原来是字母"这句话。
```

**要注意使用|符号，可以实现查找多个关键词并替换**

例如：

```
str.replace{/傻逼|煞笔|sb/ig,"**"}

将多个违禁词都替换成**
```



### 29 change 事件

表单内容发生变化 该事件发生

用于表单验证





### 30  classList.contains()函数

确认 该元素的类单中有没有某个类 ，如果有就返回true 没有就返回false







## 1 作用域和作用域链

#### 1.1 局部作用域

在函数内部和大括号内部声明的变量只能在函数内部访问

**（使用const和let的）**

分为**函数作用域**和***块作用域***（被大括号包着的）



**var定义的是全局变量** 因此不受作用域限制。



#### 1.2  全局作用域



尽量少声明全局变量防止变量污染 



#### 1.3 作用域链

实质 是变量查找机制  先查找当前函数作用域变量

如果找不到 **则逐级查找父级作用域（冒泡）**

**子作用域可以访问父作用域**







#### 1.4 垃圾回收机制



生命周期为：**内存分配、内存使用、内存回收**

全局变量的声明周期一般是**关闭网页**



**简单数据类型：存放在栈中**

**复杂数据类型：数据存放在堆中 栈中保存一个指向该堆区的指针**



内存泄漏：程序中分配的内存由于某种原因 **程序未释放 或者无法释放** 



回收机制：

- 1  引用计数法（过时）

对于每个函数或者变量 存储引用次数的内部属性

当在整个程序中引用次数为0 的时候 就释放内存 清除垃圾

**局限：**出现两个对象或者函数相互引用 易发生内存泄漏



- 2  标记清除法：

扫描从根部出发可到达的对象 凡是可以到达的对象都保留

无法到达的对象 就被清除







#### 1.5 闭包

目的：封装数据 实现数据安全私有   同时保证外部可以访问内部的数据

一个函数对周围状态的引用捆绑，内层函数访问其外层函数的作用域

**闭包=内层函数＋外层的函数中的变量**



写法：

```
function orter()
{
let count=0
    function fn()
    {
    console.log(count)
    }
return fn    
}

const func=orter()

func()  //这样就可以通过调用func函数实现对orter内部变量的访问
```



局限性：易出现  内存泄漏问题



#### 1.6 变量提升

**出现在var 声明的变量中**

实质：

j s代码执行的时候 会先扫描所有的var并留出空间

因此在 先使用var声明的变量 再声明  程序不会报错。





## 2  函数高级

#### 2.1 函数提升 

function关键词和var 一样

在执行的时候会先将function的声明 最先执行

**函数提升能使函数的声明调用更加灵活  但是函数表达式不存在提升**





#### 2.2 函数的参数

**1 剩余参数**

优点：可以设置至少有几个参数  并接受的参数数量无上限）

语法：（以sum函数为例）

```
function sum(a,b,c,...arr)
{
    let ans=0
    
    ans=a+b+c
    
    for(let i=0;i<arr.length;i++)
    {
        ans+=arr[i]

    }
    return ans

}
```

该函数就**限定了至少要传入三个参数  三个之后的参数进入...arr剩余参数**



arr实质上是一个**真数组** 作用域在函数内。





 **2 动态参数**

语法：（以sum函数为例）

```
funvtion sum()
{
 let ans=0
 
 for(let i=0;i<=arguments.length;i++)
     {
       ans+=arguments[i]
      }
 return ans

}
```

arguments实质是伪数组 只有length可以使用

缺点：无法限制最低数量的参数





**3 展开运算符**

...

就是将一个数组展开并传参。

使用场景  求数组最大值最小值 合并数组等

```
最大值：
let maxx=Math.max(...arr)

最小值
let maxx=Math.min(...arr)

合并数组
let newarr=[...arr1,..arr2]
```





#### 2.3 箭头函数

省略function的简写形式

 

```
const sum=(a,b) => {
    console.log(a+b)
}
```



##### 注意事项

**1 如果传入参数有且仅有一个 则可以省略小括号**



```
const double= a =>{
    console.log(a*2)
}
```

只有一个参数 省略小括号





**2 如果执行代码只有一句 可以省略大括号**

**并自动将其作为返回值返回。**

```
const form=document.querySelector('form')
form.addEventListener("click",ev=>ae.prventDefult())
```



**3 箭头函数可以直接返回一个对象**

```
const fn= name =>({username:name})
```

需要在箭头后面加个小括号 表示是要生成一个对象





**4 箭头函数里面没有arguments  只有剩余函数**





**5 箭头函数的this值**

之前的函数 的this是根据**它是如何被调用的从而定义函数的this值** 

而箭头函数**不会去创建自己的this**  它从自己的**作用域的上一层**去使用this

在dom事件回调函数中 使用箭头函数  出现的this指向window  不推荐







## 3 解构

#### **3.1 数组解构**

使用场景

**1 批量把数组中的各个元素按顺序分配给多个变量** 

```
const arr=[1,2,3]

const [a,b,c]=arr
```

典型应用：

交换两个变量

```
let a=1
let b=3 ;
[b,a]=[a,b]

```

注意点：

在 j s 编译的时候 如果**某行的开头是[**元素1，元素2...] 形式

在前一行一定要**记得加分号**

否则会编译识别错误



#### 各种情况：

**1 变量少 单元值多 使用剩余参数 ...arr**



```
const [a,b,...c]=[1,15,14,7,6,5]
```

...c中存储了剩下的数据 防止数据损失





**2 变量多 单元值少  使用预设值反正出现undefined**

```
const [a=1,b=2,c=2]=[2.5]
```

设置默认值



**3 二维或者多维数据转一维**

```
const [a,b,[c,d]]=[1,2,[3,4]]
```

和要被解构的数据格式相同即可



#### 3.2 对象解构



**类似数组解构  对象属性的是要赋给与属性名相同的变量**  



**要注意解构的变量名不要和外面的变量名冲突**



**使用的是大括号！！！**！

```
const user={
       name:"xiaoming",
       age:18
          }

const {name,age}=user
```

 

如果注意解构的变量名和外面的变量名冲突 **解开冲突**的方法：

```
 const { uname:name,age}={uname:lee,age:18}
```



##### 多级对象结构

```
const pig={
name:lee,
family:{
        mom:'mm',
        sister:’乔治‘
        father:'dd',
        
       }
}


解构：
const {name,family:{mom,sister,father}}=pig

格式相同就行
但是调用小解构 的时候 要注明大结构的名字


```







## 4 arr的forEach方法

用来遍历数组中每个元素   只遍历 不返回

```
被遍历的数组.forEach(function(ele,index){

//函数体
})
```

参数中第一个ele必须要声明  第二个index索引  可以不写。





## 5 arr的fillter方法

用于筛选  

**return 一个新的数组**（该数组包含所有符合条件的元素）

语法：

```
被遍历的数组.filter(function(ele,index){
return 被筛选的条件
})
```

ele必写 index 可选

如果没有符合条件的 返回空数组  

不会影响原来的旧的数组



例子：

```
const score = [50, 15, 66, 85]
const newscore = score.filter(ele => ele > 60)
console.log(newscore)
```

使用了箭头函数 减少了代码量







## 6 自定义对象构造函数

类java 构造函数

比如定义一个Pig类

```
function Pig(name='lee',age=20) {
    this.name = name
    this.age = age
}
```

同样也可以设置默认值

俩约定：

1 命名是以大写字母开头。

2 只能由new操作符来执行。





同时构造函数自身的属性和方法  被成为静态属性和静态方法

声明只能在 构造函数外进行

**1 静态成员只能通过构造函数访问**

**2 静态方法中this指向构造函数**





## **7 js 内置 结构对象和内置方法**

实质上 str num Boolean和null等基本数据类型

**在js中也也进行了对象化**





#### 常用引用类型 及其内置方法

##### Object 的keys values和assign方法



 **Object**.keys(对象)和 **Object**.values(对象)

**返回一个数组** 数组各元素是该对象的各个键或者各个value



```
const arrkeys= Object.keys(pig1)
console.log(arrkeys)

const arrvaluse= Object.values(pig1)
console.log(arrkeys)


//结果：
['name', 'age', 'sayhi']
['lee', 20, ƒ]
```





**Object.assign   (要赋给的对象，蓝本对象)**

```
const smallpig = new PIG()
Object.assign(smallpig, p2)
```

实质上就是拿着蓝本对象 对要赋给的对象进行一次键值对的更新

有就更新 没有就添加





##### arr的reduce方法

reduce **返回累计处理的结果** 常用与求和

语法：

```
arr.reduce(function(prev, now){},起始值)
```

第一个参数是上一次的返回值

第二个参数是本次的元素的值

第一次执行的时候是prev是初始值



例如数组求和



```
arr.reduce((Prev,now)=>Prev+now,0)
```



其他方法：

![](C:/Users/lenovo/Desktop/暑假学习/W4/img/Snipaste_2023-09-26_19-02-12.png)





##### arr的find方法



语法：

```
arr.find(function(ele){

函数体;
return 条件；
})
```



例如找到数组中 的对象的品牌名字是华为

```
let  huaweiphone=arr.find(ele=>ele.tagName==="华为")
```

返回的 是满足return条件的 arr中的第一个元素







##### arr的some和every方法



语法：

```
arr.every(function(ele){
return 判断语句
})
```

例如判断一个对象数组里面是不是价格全部大于50块



```
let flag = arr.every(ele=>ele.price>=50)
```





some方法和every使用相同 

**some方法是数组中只要有一个符合条件  就返回true**

**注意！！！！如果数组为空     那么every和some在一切情况下都会返回ture**





##### 伪数组转真数组 的Array.from()静态方法

例如：

```
const truearr=Array.from(document.querrySelectAll('li'))
```

**querrySelectAll返回的伪数组转换为数组后就可以使用数组的内置方法**





##### String常用方法

![](C:/Users/lenovo/Desktop/暑假学习/W4/img/Snipaste_2023-09-26_19-56-51.png)







**String方法split  字符串分割**

return一个数组

```
const str="a,b,c"
const arr=str.split(",")
```



**String方法startWith  判断开头**

return true或者false

```
const str="原神启动！！"

str.startWith("原神")  //true
str.startWith("启动")  //false

后面还可以加第二个参数 index  决定从第几个索引开始 判断

str.startWith("启动"，2)  //true
```

**相近方法：str.endWith()**



**String方法  substring()字符串截取**

```
const newarr=str.substring(5) //从第五个索引开始截取字符串到末尾

const newarr=str.substring(5，8) //从第五个开始截到第七个  第八个不截取。

```





**String方法  includes()判断子字符串**



返回true或false。

```
const str1="原神启动！！！"
const str2=“原神”

console.log(str1.includes(str2)) //ture
```





Number 的toFixed（）方法

设置精确的位数  四舍五入

```
const  number=114.156
let new=number.toFixed(2)

//114.15
```

 









## 8 JS的面向对象编程





**类java c 类的面向对象**  

**但是 对象的构造函数中内置方法 会存在浪费内存的问题**



#### **8.1 原型 prototype**

通过原型分配的函数 是所有对象所共享的

把不变的方法直接定义在protoytype上 实现方法共享:

例如  自定义arr的原型函数



```
const arr=[1,5.98,4]

Array.prototype.myMax=function()
{
return Math.max(...this)
}


Array.prototype.myMin=function()
{
return Math.min(...this)
}

Array.prototype.mySum=function()
{
return  this.reduce((prev,now)=>prev+now,0)
}

```

注意：构造函数和原型对象中的**this都指向了实例化的对象**。





#### 2 构造函数 实例对象和原型 prototype之间的关系 



**prototype和实例对象**里面会有 **属性constructor** 该属性指向构造函数

而实例对象 中还有属性_ _proto_ _   该属性指向它的原型prototype

指向 构成该原型prototype的 构造函数 

例如：

```
function Pig(age,name)
{
    this.age=age
    this.name=name
}

const p1= new Pig(18,"LEE")

console.log(p1.__proto__)//返回原型

console.log(p1.__proto__.constructor)//返回构造函数 f:Pig(age,name)

console.log(p1.constructor)//返回构造函数 f:Pig(age,name)
```

注意点：

1 _ _ proto_ _是js非标准属性  同时是readonly属性

2  [[prototype]]和_ _ proto_ _意义相同

3  如果要给构造函数的prototype 添加多个方法 使用大括号的时候 一定要在**内部手动添加constructor属性** 防止原来的内容被覆盖





## 8.3   原型继承与原型链

在本身的构造函数之上 再去继承别的类 使之成为该构造函数的父类。



注意 **每次继承操作后  要将本身的构造函数的prototype的constructor属性重新指向该构造函数本身**。

语法：

```
function Dad(){
this.属性1=value1
}
、
function Son()
{
相关属性...
}

Son。prototype=new Dad()

Son.prototype.constructor=Son
```

被称为基于原型对象的继承



**使得不同构造函数的原型对象以一种链状形式关联在一起 被称为原型链**



**元素属性在原型链上的查找规则**：



自身==》 它的原型==》 原型对象的原型==》 一直查找到Object为止





**instanceof 运算符**



a   instanceof  b

**检测a的原型链上有没有 b**

**返回Boolean值。**

```
console.log(p1 instanceof Pig)  //ture
console.log(p1 instanceof Array) //false
console.log(p1 instanceof Object) //ture
console.log(简单数据类型 instanceof Object) //false

```







## 9 浅拷贝和深拷贝



#### **9.1 浅拷贝**

拷贝的是地址

只能用**于内部全是简单数据类型**的拷贝

如果是**简单**数据类型则 拷贝**值**  如果内部子元素是**复杂数据**类型 拷贝**地址**

（单层对象，没问题 ，多层对象就有问题。）

常见方法

```
const obj={
name:"lee",
age:10
}

const newobj={...obj}
// 使用...展开

const newobj={}
Object.assign(onj,newobj)
// 使用Object的assign方法实现浅拷贝。
```



#### 9.2 深拷贝

拷贝的是对象 不是地址。

实现方法：

##### 1 递归实现

```
const obg={age:18,
    money:[50,57,55],
    family:{
        son:'lee',
        dad:'bob'
    }
}
const newobj={}
//给定原始数据  创建要被克隆的对象


function  deepcopy(newobj,old)
{
    for (let k in old) {
        if (old[k] instanceof Array)
        {  newobj[k]=[]
            deepcopy(newobj[k],old[k])
        }

        else if (old[k] instanceof Object)
        {
            newobj[k]={}
            deepcopy(newobj[k],old[k])
        }
        else
        {
            newobj[k]=old[k]
        }

    }
}
// 定义深拷贝函数

deepcopy(newobj,obg)
//调用
console.log(newobj)
```

注意事项：

1 每次递归前都要**先创建一个新的 []或者{}** 去承接再次调用时的获得数据

2  instanceof  **判断要先判断Array 再去判断Object**  

因为Array类也属于Obj类 **要注意顺序**



##### 2  调用lodash库函数

```
const new1 = _.clone(obg)
```





##### 3 JSON转换 

```
const new1 = JSON.parse(JSON.stringify(obg))
console.log(new1)
```









## 10 异常处理



#### 1 throw

throw 抛出异常 并**中断程序的执行**

在console中显示错误信息

常常和catch搭配使用



#### 2 try catch  finally

catch捕获异常后

如果不加throw  **程序继续执行**(finally模块和接下来的代码都执行)

加上throw  **程序中断**（只执行 finally模块）





#### 3 debugger



相当于在控制台上

打上断点标记





## 11 this 自定义





#### 11.1 apply和call函数

特点：

在改变this'指向的同时  执行该函数



语法：

```
fun.call(this指向，参数1，参数2...)

fun.apply(this指向，数组[])
```

其返回值就是函数的返回值 其实质就是在执行函数





#### 11.2 bind函数

特点：改变this的值 但是不执行函数  实质是克隆生成了一个this改变的类似函数

语法：

```
fun.bind(更改后的this指向)
```

其返回值是  克隆出来的 **原函数的拷贝（新的函数）**

应用：改变定时器内部的this指向

```
btn.addEventListener('click',function(){
this.disabled=true
setTimeout(function(){
this.disabled=false
}.bind(btn),60000)
})
```

在setTimeout定时器里面 this原本指向的是window 

 **需要通过bind函数更改this指向**





## 12 防抖

**单位时间内 频繁触发的事件 只执行最后一次**

**使用场景：搜索栏   表单输入验证**



#### 方法1：lodash内置函数



```
_.debounce(要执行的函数，事件停止多少秒)
```



例如鼠标移动的事件监听器：

```
box.addEventListener("mousemove", _.bebounce(fn,500))
```

鼠标停止移动500毫秒后再执行

这里addEventLintener的第二个参数     传入的就是lodash内置函数







#### 方法2：  手写函数

定义定期器变量，每当事件被触发，

先判断此时有无定时器  有的话就删掉原来那个定时器

如果没有定时器 就开启定时器。

定时器内调用要执行的函数。

```
function deboune(fn,t)
{
    let timer
    return function (){
        if(timer) clearInterval(timer)
        timer=setTimeout(function (){
            fu()
        },t)
    }
}
btn.addEventListener('click',deboune(function () {
    500毫秒后要执行的函数体
},500))
```







## 13 节流**throttle**



和防抖的区别：

防抖 ：单位时间内 频繁触发事件 只执行最后一次

节流：单位时间内  频繁触发事件  只执行一次 

**防抖：表单格式验证等**

**节流：鼠标移动mousemove  页面尺寸缩放 滚动条滚动scroll等**



#### 方法1：lodash内置函数

和防抖很相似  

```
_.throttle(要执行的函数，事件停止多少秒)
```

例如鼠标移动的事件监听器：

```
box.addEventListener("mousemove", _.throttle(fn,500))
```



每500ms 只执行一次该函数  

这里addEventLintener的第二个参数     传入的就是 lodash内置函数





#### 方法2：手写节流函数

每次监听到事件 先判断有无定时器 如果没有定时器  setTimeOut

如果有  就不开启

```
function throttle(fn,t)
{let timer =null
return function ()
    if(！timer){
    timer=setTimeout(function()
    {
    fn()
    timer=null
    },t)

    } 
}

//在setTimeout中是无法删除使用clearTImeout（timer）
删除方法：timer = null
```





## 14  补充：视频事件ontimeupdata和onloadeddata



**ontimeupdata 表示视频的播放位置发生改变的时候 触发的事件**



**ontimeupdata 表示每次进入视频的该页面  视频从哪里开始加载**



通过localStorage 存储视频的currentTime属性



再下次打开网页的时候监听ontimeupdata事件  

触发时将视频currentTime属性移动到上次记录的值 

可以实现视频播放记忆定位



**但是ontimeupdata 的触发频率很高  因此使用throttle节流优化**















## 15  arr的orderBy方法实现排序

使用方法：

```
import _ from "lodash"; //先  导入 lodas包


使用：
_.orderBy(arr,"date","desc")

```

三个参数  第一个参数是被排序的数组  第二个参数是数组内部的属性  用来排序的依据

第三个参数决定是升序还是降序    "desc"降序         "asc"升序

返回值就是一个新的排过序的数组