# 一、概述

1. git网址：https://github.com/edu2act/course-javascript-advanced

2. about:blank 打开空白页面

3. Ctrl + R 刷新；

   Ctrl + L 清空之前内容；

   Ctrl + 鼠标滚轮 放大；

   shift + enter 输入过程中的换行

4. console.error(5)  输出错误

5. 调试代码

6. JavaScript是一种直译式脚本语言

# 二、JS数据类型、值与类型转换

## 1、存储过程

1. 基础数据类型存储过程（String、Number、Undefined、Null、Boolean

   值类型，两个变量的存取不会产生影响，存储在栈区

2. 对象的存储存放在堆区，通过引用，两个相互赋值的值会相互影响

```javascript
/**************基本数据类型和引用类型的区别*****************/
/*一、赋值时不同*/
	//基本数据类型
        var num1 = 20;
        var num2 = num1;
        num1=10;
	//引用型数据类型：对象、数组
        var obj1 = {"username":"zhangsan"};
        var obj2 = obj1;
        obj2.username = "lisi";
        console.log(obj1);//lisi
        obj1.username = "wangqu";
        console.log(obj2);
        console.log(obj1);
        //obj1和obj2指向同一片堆区，值相互影响
        var arr1 = [1,5,9];
        var arr2 = arr1;
        console.log(arr2);
/*二、判等时不同*/
	//基本数据类型
        // == 判断值是否相等
        // === 判断值和数据类型是否相等
        var a=10;
        var b=10;
        console.log(a==b);//true
	//引用数据类型
        var obj1={};
        var obj2={};
        console.log(obj1==obj2);//false
```

## 2、数据类型检测方法（typeof、instanceof）

- typeof有：string、number、Boolean、undefined、object、function

## 3、基本数据类型的值

- Number类型的值
  - 整数与浮点数
  - NaN、isNaN、Infinity（正无穷）、-Infinity、+0、-0
- String类型的值  学习网站https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/split
  - split （分隔符，生成数组的元素个数）将字符串以特定分隔符分割，生成数组
  - slice （）与substr用法相同
  - substr（截取的起始位置，截取的长度）
  - 空字符串、字符和字符串、转义字符
- Boolean类型的值
  - true、false
- Null与Undefined
  - null、undefined

## 4、包装对象

```javascript
// var str = new String('mxy');
var str1 = 'mxy';
str1.substr(0,2);
/*相当于装箱操作*/
var str1 = 'mxy';
var strObject = new String(str1);
strObject.substr(0,2);
```

