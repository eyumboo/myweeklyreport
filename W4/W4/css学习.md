## 1 定位

**定位=定位模式+边偏移**

##### 1.1定位模式

absolute是绝对定位，relative是相对定位

css默认是absolute绝对定位





**position：absolute（拼爹系）：**

是参照**ralative型最近一级的祖先元素**的，配合TOP、RIGHT、BOTTOM、LEFT(下面简称TRBL)进行定位，**在没有设定TRBL，默认依据父级的坐标原始点为原始点。**

如果设定TRBL并且父级没有设定position属性，那么当前的absolute则以浏览器左上角为原始点进行定位，位置将由TRBL决定。

absolute**是脱标的 不占有原来的位置** 高度**z-index比浮动流更高**





**position：relative（自恋型）**：相对定位，**参照该元素的原始点进行移动**，配合TRBL进行定位。

虽然位置发生了移动，但是原来 的位 置还是保留  脱标

float浮动原来的位置不保留  脱标

**经典作用：作为绝对定位的父元素**





##### 1.2 子绝父相

如果子元素要用绝对定位 那么父元素就要用相对定位





##### 1.3 固定定位 position：fixed

以**可视窗口作为 原始点** 配合TRBL进行定位

技巧：固定在内部元素的box盒子版心右侧

```
.fixed_box
{
left:50%;
margin-left：盒子宽度的50%;    
}
```



##### 1.4 z-index属性

z-index的值越大，飘得越高

**但是父元素的index 一定小于子元素**

**只有定位才有z-index属性  标准流和浮动没有**





##### 1.5 margin;auto 和 position:absolute的冲突



解决方法：

水平居中：

```
.box{
position:absolute;
left:50%;
margin-left:-盒子宽度的一半px;  //注意是负值
}
```

垂直居中

```
.box{
position:absolute;
top:50%;
margin-topt: -盒子宽度的一半px;  //注意是负值
}
```





##### 1.6 postiton后设置宽高的问题

**行内元素添加定位后 可以直接设置宽和高**

 **块元素添加定位后 自动转化为行内块元素**





## 2 滚动条

让滑动丝滑



```
html  {
scroll-behavior:smooth;
}
```

