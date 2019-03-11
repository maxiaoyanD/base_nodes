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

2. 对象的存储存放在堆区或栈区，通过引用，两个相互赋值的值会相互影响

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
/*装箱：*/
// var str = new String('mxy');
var str1 = 'mxy';
str1.substr(0,2);
/*相当于装箱操作*/
var str1 = 'mxy';
var strObject = new String(str1);
strObject.substr(0,2);
```

# 三、基本（原始）数据类型进阶

## 3.1、Number进阶

3.1.1、装箱过程

​	基本数据类型，在操作过程中，会有自动装箱过程，生成临时对象，临时对象会在使用完成后自动释放。

​	注：访问对象属性时，首先访问自身属性，访问不到时则会在原型链上寻找对应的属性和方法。

3.1.2、Number原型方法，构造器属性

```javascript
			/*Number进阶*/
			var num = 10;
			num.toString();

			var num = 10;
			var numObject = new Number(num);
			numObject.toString();
			num.p = 10;
			var t=num.p;
			console.log(t);//undefinded

			//toFixed(x):保留记x位小数
			var num1 = 11.29;
			var numobj2 = new Number(num1);
			console.log(numobj2);
			num1.toFixed(1);//11.29
			//toPrecision(x):转换为指数
			var n1 = 12345.6789;
			console.log(n1.toPrecision(2));
			//toString():转换为字符串
//Number构造器属性（静态属性）
Number.MAX_VALUE
Number.MIN_VALUE
Number.NaN
Number.NEGATIVE_INFINITY
Number.POSITIVE_INFINITY

//Number原型方法(Number对象继承的方法）

//Number._proto_  :所有的方法都构造在他之上

// Number.prototype.toFixed();
// Number.prototype.toPrecision();
// Number.prototype.toString();
// Number.prototype.toExponential();

			//基本数据类型的__proto__属属性
			// ==（和）
			//变量构造函数的prototype是相等的
			var n = 20;
			console.log(n.__proto__);
			console.log(n.prototype);
```

## 3.2、String进阶

3.2.1、字符串比较

```javascript
//A.localeCompare(B):字符串比较
'b'.localeCompare('a')//1
```

3.2.2、字符串拼接

- 合并：加号运算法（+、+=）
- 合并：拼接字符串数组（通过数组方法push，join等）

3..2.3、字符串构造器方法

```javascript
//String.fromCharCode(97,98,99)：将数字转换为字符
String.fromCharCode(97,98,99);//"abc"
String.fromCharCode.apply(null,[97,98,99]);//"abc"
```

3.2.4、字符串原型方法之提取字符串

```javascript
var str1 = "abcdjhfe";
//str.charAT(index)：返回特定索引位置的字符
console.log(str1.charAT位置的字符的Unicode码(3));//d
//str.charCodeAt(index):返回特定索引
console.log(str1.charCodeAt(3));
//slice(起始位置，截止位置)：截取
console.log(str1.slice(0,3));
str1.slice(1,-1)
//substr(截取的起始位置,截取字符串的长度):
str1.substr(0,3);
str1.substr(0,-1);//""
//substring(截取起始位置，截取截止位置):截止位置可不写
//如果sunstring起始位置>结束位置会自动交换位置substring(3,0)
//substring(0,-1)和slice(0,-1)是不一样的
//如果超出索引范围自动截断substring(-1,3)
str1.substring(0,3);
//split(特定的字符,(长度)):以特定的字符分割成数组,长度可选可不选
var str2 ="a*c*g/h*f";
str2.split("*");
str2.split("*",2);
```

3.2.5、字符串原型方法之字符串变换

```javascript
var ss = "     abc  d     "
//trim():去除字符串两边的空格，字符串内部的空格不去除
ss.trim();//"abc  d"
//concat(str1,str2):将字符串拼接起来
var str3 = "hello ";
str3.concat("world");//"hello world"
//
```

3.2.6、字符串原型方法之检索和比较

3.2.7、字符串原型方法之可正则方法

## 3.3、Boolean进阶

3.3.1、所有对象都是真值

# 4、JS语法、表达式及语句

4.1、JS语法、表达式及语句综述

4.1.1、字面量

4.1.2、标识符与保留字

4.1.3、表达式与语句

# 5、JS赋值、算数、关系运算符

## 5.1、JS赋值运算符

表达式要发反写（a = 45）

```javascript
var a = 34;
if(a = 45){
    console.log("是否会输出？");
    //会输出，a=45
}
var b = 34;
if(45 == b){
    //为什么要这样写，有什么好处
    //表达式要发反写，防止=和==判等出错
    console.log("是否会输出？");
}
```

## 5.2、JS算数运算符

```javascript
//带有字符串的+表示拼接
//有对象的+将类型转换成对象
//其余有+转换成数值类型
//带有字符串的-，将字符串转换为数值类型
console.log("1"+"2");//"12"
console.log("1" + 2);//"12"
console.log(1+{});//"1[object Object]"
console.log(true + true);//2
console.log("5" - 2);//3

var x = "1";
console.log(++x);//2
//注意：++和--的隐式类型转换
//++x 输出是2 x++输出的是"1"
var x="1";
console.log(x+1);//"11"
//思考：+= 是转换成字符串类型还是转成数字类型
//不同情况下转换的类型不同
var x="1";
console.log(x+=1);
// ==> x=x+1 ==> "1"+1 ==> "11"
var x=1;
console.log(x+=1);//2

//回顾 ++i 和 i++
var i=1;
var y = ++i + ++i + ++i;
console.log(y);
// ==> 2 + 3 +4 ==>9
```



## 5.3、JS关系运算符

# 6、JS逻辑运算符进阶

## 6.1、&&与||的基本理解应用

运算符两边的操作数都是布尔类型

对于&&来说：全真为真，一假为假

对于||来说：全假为假，一真则真

## 6.2、&&与||的非布尔类型

**短路原则**：

&&短路原则：左真右，左假左

||短路原则：左真左，左假右

**注意：**

​	所有的对象转换为布尔类型都是真的，{}空对象转换为布尔类型是真

## 6.3、&&和||在实际中的应用

- 遵循短路特性，使用&&和||可用来实现条件语句

  ```javascript
  /**************2019/03/11 *************/
  var score = 76;
  if(score>90){
      console.log("优");
  }else if(score>75){
      console.log("良");
  }else if(score>60){
      console.log("及格");
  }else{
      console.log("不及格");
  }
  
  //通过&&和||的组合实现如上功能
  //注：小括号的优先级最高
  console.log((score>90&&"优")||(score>75&&"良")||(score>60&&"及格")||"不及格");
  ```

- 使用||来设置函数的默认值

  ```javascript
  /******************219/03/11 *****************/
  var sum = function(a,b,c){
      b=b||4;
      c=c||5;
      return a+b+c;
  };
  //未传参的话，形参初始值为undefined，
  //undefined转换为布尔类型为false，根据短路原则直接返回值
  console.log(sum(1,2,3));
  // ==> 1 + 2 + 3 ==> 6
  console.log(sum(1,2));
  // ==> 1 + 2 + 5 ==> 8
  console.log(sum(1));
  // ==> 1 + 4 + 5 ==> 10
  console.log(sum(1,0,0));
  // ==> 1 + 4 + 5 ==> 10
  ```

- sum函数的问题及完善

```javascript
var sum = function(a,b,c){
    if(b!=false){
        b = b || 4;
    }
    if(c != false){
        c = c || 5;
    }
    return a+b+c;
}
//undefined != false 是true
// 0 == false
console.log(sum(1,2,3));
// ==> 1 + 2 + 3 ==> 6
console.log(sum(1,2));
// ==> 1 + 2 + 5 ==> 8
console.log(sum(1));
// ==> 1 + 4 + 5 ==> 10
console.log(sum(1,0,0));
// ==> 1 + 0 + 0 ==> 1
```

