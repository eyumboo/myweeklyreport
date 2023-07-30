java前置知识基本已经学习完毕

本周重点学习了

  **1 java函数index（）**

index() 函数用于从列表中找出某个值第一个匹配项的索引位置。

注意从位置是从0开始的

例：

```
l=[“an”,“Aynor”,1,3]
l.index(1)
output：2
l.index(3)
output：3
l.index(“an”)
output：0
l.index(“Aynor”)
output：1 
```



**2 java函数indexOf（）**

返回指定字符串中指定字符或字符串第一次出现的位置。

String 类的 indexOf() 方法在字符串中查找子字符串出现的位置，

如果存在返回字符串出现的位置（第一位为0），如果不存在返回 -1：

![屏幕截图 2023-07-30 214704](C:\Users\lenovo\Desktop\暑假学习\W1\img\屏幕截图 2023-07-30 214704.png)

```
public class Test2 {
    public static void main(String args[]){
        String s1="this is index of example";
//传递子串
        int index1=s1.indexOf("is");//返回子字符串的索引
        int index2=s1.indexOf("index");//返回子字符串的索引
        System.out.println(index1+"  "+index2);//2 8

//使用指定索引开始传递子字符串
        int index3=s1.indexOf("is",4);
        System.out.println(index3);//5
        int index4=s1.indexOf("is",20);
        System.out.println(index4);//-1 没有找到子串

//传递字符值
        int index5=s1.indexOf('s');
        System.out.println(index5);//3
    }
}
```

输出：

```
2  8

 5 

-1

 3
```

   



  **3   stringbulider的使用**

继承自抽象类AbstractStringBuilder。

运行速度  StringBuilder  > String。

**String**字符串是不可变

而**StringBuilder**类代表可变字符串对象。

它可以通过调用append（）方法实现对字符串对象的改变

## StringBuilder和String相互转换：

（1）Stringbuilder——>String：
publilc String toString():通过toString（）就可以实现吧StringBuilder转成String。
（2）String——>StringBuilder：
通过构造方法StringBuilder（String str）直接转换。





**4 java基类Object**

Object类是Java`java.lang`包下的核心类，

**Object类是所有类的父类**，何一个类时候如果没有明确的继承一个父类的话，那么它就是Object的子类；

相关方法：

**clone()**

保护方法，实现对象的浅复制，只有实现了`Cloneable`接口才可以调用该方法，否则抛出CloneNotSupportedException异常。

**toString()**

该方法用得比较多，一般子类都有覆盖，来获取对象的信息。

**. equals()**

比较对象的内容是否相等

 **hashCode()**

该方法用于哈希查找，重写了equals方法一般都要重写hashCode方法。这个方法在一些具有哈希功能的Collection中用到。