# 1、概述

1. git网址：https://github.com/edu2act/course-javascript-advanced

2. about:blank 打开空白页面

3. Ctrl + R 刷新；

   Ctrl + L 清空之前内容；

   Ctrl + 鼠标滚轮 放大；

   shift + enter 输入过程中的换行

4. console.error(5)  输出错误

5. 调试代码

6. JavaScript是一种直译式脚本语言

# 2、JS数据类型、值与类型转换

## 1、存储过程

1. 基础数据类型存储过程（String、Number、Undefined、Null、Boolean

   值类型，两个变量的存取不会产生影响，存储在栈区

2. 对象的存储存放在堆区或栈区，通过引用，两个相互赋值的值会相互影响

   **？？栈区存引用，堆区存内容？？**

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

# 3、基本（原始）数据类型进阶

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

```javascript
/*********字符串原型方法之检索和比较***********/
//str.indexOf(stringValue):返回查找字在被查找字符串中初次出现的位置，如果不存在则返回-1
var str4="你好吗好好";
var str5="哈哈哈哈或 '你好吗好好'很啦"
str4.indexOf("好");//1
//str.lastIndexOf(stringValue):返回最后出现的位置，如果不存在返回-1
str4.lastIndexOf("好");//4
//"a".localeCompare('b'):判断a是否在b之前，如果是返回整数，不是返回负数
str4.localeCompare('啦');
```

3.2.7、字符串原型方法之可正则方法

## 3.3、Boolean进阶

**所有对象都是真值**

# 4、JS语法、表达式及语句

## 4.1、JS语法、表达式及语句综述

4.1.1、字面量

4.1.2、标识符与保留字

4.1.3、表达式与语句

## 4.2、JS严格模式

## 4.3、switch详解、for....in

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

​	**== 和 ===的区别**

==：如果类型不同，先转换再比较（引用类型转换成数据类型）

===：类型不同为false，若类型相同再判断

```javascript
console.log(3==new String(3));//true
console.log(3===new String(3));//false

//下列中的false，
/**需要好好思考 **/
var obj1 = new String("xyz");
var obj2 = new String("xyz");
console.log("xyz" === obj1);//false,类型不同
console.log(obj1 == obj2);//false
console.log(obj1 === obj2);//false
console.log(obj1 == new String("xyz"));//false


console.log(NaN === NaN); //false
console.log({} === {});//false
```



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

# 7、JS函数及函数参数

## 7.1、函数的定义与调用

### 7.1.1、函数的定义方式（3）

1. 通过函数声明的形式来定义
2. 通过函数表达式的形式来定义（可以是没有函数名的匿名函数，有名的话方便调用栈追踪）
3. 通过function构造函数实例化的形式来定义（JS中函数也是对象，函数对象）

```javascript
//1、函数声明方式
function max(a,b){
    return a>b?a:b;
}
max(2,3);

//2、函数表达式方式 
//等号右侧可以是匿名函数也可以是非匿名函数
//注意：函数调用不可以放在函数声明之上
var max = function(a,b){
    return a>b?a:b;
}
max(2,3);

//3、用function构造函数
//function实例化函数，执行效率相对较低，但是更加灵活
 var max = new Function('a','b','renturn a>b?a:b');
 max(1,2);
```

### 7.1.2、函数的调用方法（4）

```javascript
//四种调用方式
//1-作为函数直接调用
    //（非严格模式下this为全局对象，严格模式下为undefined） 
    function test(){
        console.log(this);
    }
    test();//这里的this指的是window


//2-作为方法调用（this为调用方法的对象）
    var obj ={
        x:0,
        test:function(){
            console.log(this.x);
        }
    };
    obj.test();//0

//在普通函数调用，this指向全局对象
//当函数不作为对象的的属性调用时，就相当于普通函数，this指代的是全局对象
//当他作为对象的属性调用时，指该对象
//例一
var x = 45;
var test = function(){
    console.log("输出：",this.x);
}
var obj = {
    x:23
}
obj.test = test;
obj.test();//23
test();//45
//例二
var x = 45;
var obj = {
    x:23,
    test:function(){
        function foo(){
            console.log(this.x);
        } 
        foo();
    }
}
obj.test();

//给obj动态添加方法
var obj ={
    name : 'jsck'
}
var sayHi = function(){
    console.log("Hi,i'm",this.name);
}
obj.sayHi = sayHi;//给对象添加方法
obj.sayHi();//Hi,i'm jack

//思考如下代码 详情参见高阶函数函数章节
var x=55;
var obj=function(){
    name:'hhh'
}
var fun1 = function(){
    return function fn2(){
        return this.x;//若改为return this;
    }
};
obj.fun3 = fun1;
obj.fun4 = fun1();
console.log(obj.fun3());//fun2函数 √
console.log(obj.fun3()())//55 √
console.log(obj.fun4())//我以为的结果是55，实际结果是undefined
/**
 * 改为return this
 * console.log(obj.fun3());//fun2函数
 * console.log(obj.fun3()())//window
 * console.log(obj.fun4())//ƒ (){name:'hhh'}
*/

//3-通过call()和aplly()间接调用
    //(this为函数对象的call/apply方法的首个参数，移花接木)
    objA = {"name":"AA"};
    objB = {"name":"BB"};
    objA.foo = function(){
        console.log(this.name);
    }
    objA.foo();//AA
    //方法名.call()可以切换调用的对象
    objA.foo.call(objB);//BB
    objA.foo.apply(objB);//BB

//4-作为构造函数调用（this指向实例化对象）
    //构造函数的函数名要大写
    function Person(name){
        this.name = name;
    }
    Person.prototype.sayHi = function(){
        console.log("hi" + this.name);
    }
    var person = new Person("mamama");
    person.sayHi();
    console.log(person.__proto__ === Person.prototype);

```

## 7.2、函数参数的数量问题

```javascript
//实参大于形参
//通过函数对象的属性arguments获得所有实参、类数组对象
function test(){
    console.log(arguments);
    console.log(test.arguments == arguments.arguments);//false
    console.log(arguments.length);//4
    console.log(typeof arguments);//Object
    console.log(arguments instanceof Array);//false
    console.log(arguments instanceof Object);//true 
    console.log(Array.prototype.slice.call(arguments));//["Hello",",","World","!"]
    var s = "";
    for(var i=0;i<arguments.length;i++){
        s += arguments[i];
    }
    return s;
}
test("Hello",",","World","!");

//实参小于形参 
//少的参数值为undefined，可以引用||来给出默认值

var sum = function(a,b,c){
    b = b||4;
    c = c||5;
    return a+b+c;
}
console.log(sum(1,2,3))//6
console.log(sum(1,2));//8
console.log(sum(1));//10
```

## 7.3、参数类型与传递方式（值、引用）

```javascript
//值传递
 //实参为基本数据类型时，参数改变不影响实参
 var a = 1;
 function foo(x){
     console.trace("a:",a,"x:",x);//a:1,x:1
     x=2;//step 22222
     console.trace("a:",a,"x:",x);//a:1,x:2
 }
 console.trace("a:",a);//a:1
 foo(a);//step 111111
 console.trace("a:",a);//a:1


 //引用传递
 //实参为引用数据类型时，形参改变影响实参
 var obj = {x:1};
 function fee(o){
     console.trace("obj.x:",obj.x,"o.x",o.x);//1,1
     o.x = 3;
     console.trace("obj.x:",obj.x,"o.x",o.x);//3,3
 }
 console.trace("obj.x:",obj.x);//1
 fee(obj);
 console.trace("obj.x:",obj.x);//3
```

# 8、JS函数对象

## 8.1、函数对象

## 8.2、函数对象的属性及方法

## 8.3、高阶函数

# 9、JS预解析

## 9.1、JS解析及执行简介

解析过程：

- 全局预解析阶段（全局变量和函数声明前置）
- 全局顺序执行阶段（变量赋值、函数调用等操作）
- 当遇到调用函数时，在执行函数内代码前，进行函数范围内的预解析
- 当存在函数嵌套时，以此类推，会进行多次函数预解析

## 9.2、JS预解析（声明提升）

### 9.2.1、预解析的主要工作：

变量声明和函数声明提升

解析器在执行当前代码前的进行扫描（var 、function）将变量和函数声明在当前作用域（全局、函数）内进行提升。

```javascript
//变量声明提升案例：
console.log(a);        //var a;
var a = 1;      //===>  console.log(a);
console.log(a);        //a = 1;
					   //console.log(a);

//函数声明提升案例：
foo();                  // function foo(){
function foo(){         //    console.log("f_1");
    console.log("f_1"); //}
}				//=====>  function foo(){
function foo(){	        //	  console.log("f_2");
    console.log("f_2"); //}
}						// foo();//f_2

//ES5中函数及变量声明重复分话，相当于覆盖
```

### 9.2.2、声明提升

```javascript
//①、同时有var和function关键字时(情景1：函数表达式)
foo();//报错                   //var foo = function(){
var foo = function(){         //       console.log("foo");
    console.log("foo");       //}
}							  //foo();有结果foo

//②、当function前有运算符的话，认定为表达式，不提升
//上述等效代码
var foo;                     //console.log(foo);//undefined
foo();//报错					//var foo = function(){
foo = function(){			 //     console.log("foo");
    console.log("foo");		 // };
}							 // foo();//"foo"

//③、同时有var和function关键字时（情景2：变量名和函数名同名）
AA();						//function AA(){
function AA(){				//		console.log("AA_1");
    console.log("AA_1");	//}
}                 //=======>//var AA;
var AA = function AA(){     //AA(); //AA_
    console.log("AA_2");	// AA= function AA(){
}							//		console.log("AA_2");
AA();						//AA(); //AA_2

//函数的提升在变量提升之上
```

## 9.3、预解析与作用域

### 9.3.1、JS变量作用域

变量的作用域是指变量在何处可以被访问到

全局变量和局部变量

ES5中没有块作用域，采用的是函数级作用域

# 10、JS作用域及执行上下文

## 10.1、JS作用域及特点

### 10.1.1、作用域

就是变量与函数的可访问范围（变量生效的区域范围，即在何处可以被访问到）

### 10.1.2、JS作用域及特点

JS采用的是词法作用域（静态性），这种静态结构决定了一个变量的作用域

```JavaScript
//词法作用域**不会被函数从哪里调用等因素影响**，与调用形式无关（体现了静态性）
var name = 'jack';
function echo(){
	console.log(name);//全局变量
}
function env(){
	var name = 'lili'; //此处的作用域仅限于env函数内
	echo();
}
env();//jack

//通过new Function创建的函数对象不一定遵从静态词法作用域
```

![img](file:///C:\Users\lenovo\AppData\Roaming\Tencent\Users\2390140586\TIM\WinTemp\RichOle\W1T4F]AVGN056DE_}JS{7IV.png)



## 10.2、JS执行上下文与调用栈

​	执行上下文指代码执行时的上下文环境（包括局部变量、相关的函数、相关自由变量等）

​	JS运行时会产生多个执行上下文，处于活动状态的执行上下文环境只有一个。

调用栈（Call Stack）：代码执行时JS引擎会以栈的方式来处理和追踪函数调用。

## 10.3、作用域链与执行上下文

​	执行时，当前执行上下文，对应一个作用域链环境来管理和解析变量和函数（动态性）

​	变量查找按照有内到外的顺序（遵循词法作用域），直到完成查找，若为查询到则报错

​	当函数执行结束，运行期上下文被销毁，此作用域链环境也随之被释放

# 11、JS中的IIFE模式

## 11.1、IIFE及使用方式

​	IIFE：立即执行函数表达式

**作用**：建立函数作用域，解决ES5作用域缺陷所带来的问题，如：变量污染、变量共享等问题

**写法**：（function foo(x,y){......}(2,3)）; 

​	      (function foo(x,y){......})(2,3);

**注意：IIFE是表达式，要注意使用分号结尾，否则可能出现错误。。。**

## 11.2、IIFE解决问题

​	**通过IIFE对作用域的改变（限制变量生命周期）**

Js（ES5）中没有块作用域，容易造成js文件内或文件间同名变量相互污染。可以通过IIFE引入一个新的作用域来限制变量的作用域，来避免变量污染，可以通过IIFE引入一个新的作用域来限制变量的生命周期

​	**通过IIFE对变量存储的改变（避免变量共享错误）**

## 11.3、IIFE实际应用案例

避免闭包中废弃物的变量共享问题（页面导航问题）

# 12、JS闭包（closure）

## 12.1、闭包的概念

​	闭包：由函数和与其相关的引用环境组合而成的实体，是词法作用域中的函数和其相关变量的包裹体

```JavaScript
    //闭包
    /*闭包：
        函数通过返回函数（fn1）内部定义的函数（fn2）来访问fn1
        内部的局部变量（x）
    */
    //访问fn1内部变量x,借助fn1内部定义的函数fn2来访问内部变量
    function fn1(){
        var x = 1;
        function fn2(){
            return ++x;
        }
        return fn2;
    }
    var fn3 = fn1();//得到fn2函数
    console.log(fn3());//2
    console.log(fn3());//3
//例子
function foo(){
    var i=0;
    function bar(){
        console.log(++i);
    }
    return bar;
}
var a = foo();
var b = foo();
a();//1
a();//2
b();//1
```

## 12.2、闭包的常见形式



## 12.3、闭包的作用及常用场景

# 13、JS对象综述

## 13.1、JS对象简介

​	JS对象是一个复合值，将很多值复合在一起(包括原始类型值、对象、函数)

​	JS对象是若干无序属性的集合，可以直接通过属性名来访问对象的属性（键值对）

​	函数作为某一个对象的属性时，称其为该对象的方法。

```javascript
var obj = {
    num:10,
    str:"Hi",
    show:function(){
        console.log(this.str);
    }
};
console.log(obj.num);//10
console.log(obj.str);//Hi
obj.show();			 //Hi

// 左边instanceof 右边：
/** 含义：
 * 1，左边是右边的一个实例吗
 * 2，左边的__proto__原型链上是否包含右边的prototype
*/
/**
 * 对象 instanceof 构造函数
 * 1，判断对象能否使用该构造函数实例化得到
 * 2，判断对象的原型链上能否找到该构造函数的原型
 * 对象.__proto__.__proto__.(长度不确定)==构造函数.prototype
 */
/*任何对象 instanceof Object都得true，
 *因为Object是所有对象的原型
 */
console.log(Object instanceof Function);//true
console.log(Object instanceof Object);//true
console.log(Boolean instanceof Function);//true
console.log(Boolean instanceof Object);//true
console.log(String instanceof Function);//true
console.log(String instanceof Object);//true
console.log(Number instanceof Function);//true
console.log(Number instanceof Object);//true
console.log(Function instanceof Function);//true
console.log(Function instanceof Object);//true
console.log(Array instanceof Function);//true
console.log(Array instanceof Object);//true
console.log(Date instanceof Function);//true
console.log(Date instanceof Object);//true
console.log(Math instanceof Function);//false
console.log(Math instanceof Object);//true
console.log(JSON instanceof Function);//false
console.log(JSON instanceof Object);//true
```

获取对象属性的三种方法

```javascript
var obj={
    "x":1,
    "y":2
}
console.log(obj.x);
console.log(obj['y']);
var z='age';
//1、.
obj.z=20
console.log(obj);//x:1,y:2,z:20
//2、[变量]
obj[z]=20;
//如果z变量是变量会取变量的值作为名称
//如果z是字符串就会用字符串作为名称
console.log(obj);//x:1,y:2,age:20
//3、['']
obj['z'] = 20;
console.log(obj);//x:1,y:2,z:20
```

## 13.2、JS对象的属性

​	JS的访问器属性

如果只有get方法则为只读属性，不可修改内容

如果只有set方法则为只写属性，不能读取，读取结果为undefined

实现数据属性的间接访问，可实现数据的验证、过滤、运算等功能

```javascript
var o = {
    _x:1,
    get x(){
        return this._x;
    },
    set x(val){
        this._x = val;
    }
};
console.log(o.x);//1
o.x=2;
console.log(o.x,o._x);//2 2
o.hasOwnProperty("x");//true 访问器属性
o.hasOwnProperty("_x");//true 数据属性
```

## 13.3、JS对象相关操作

### 13.3.1、创建对象（3种）

```javascript
    /*
        1、 var obj1 = {
            属性名:方法值,
            方法名:方法
        };
        2、var obj1 = {};
           var obj2 = Object.cteate(obj1);
        3、function exo(){};
           var l = new exo();
    */
```

（1）通过字面量的方式创建

```javascript
var obj = {
    num:10,
    str:"Hi",
    show:function(){
        return this.str;
    }
};
console.log(obj.num);//10
console.log(obj.str);//"Hi"
console.log(obj.show());//"Hi"
console.log(obj.__proto__);
console.log(obj.__proto__ == Object.prototype);//true

```

（2）、通过Object的create静态方法创建

```javascript
//注：JS对象是通过原型链的方式实现的对象继承
var newObj = Object.create(obj);
//newObj的原型是obj
newObj.age=23;
console.log(newObj.age);//是newObj自有的属性
console.log(newObj.__ptoto__)//obj
console.log(newObj.__proto__ == obj);//true
```

（3）构造函数创建

```javascript
/*传统的构造函数*/
    function fans(username,age){
        //这里的this指代当前函数实例化的对象
        this.username = username,
        this.age = age;
        this.sayHi = function(){
            console.log(this.username);
        }
    }
    var person1 = new fans("zhangsan",20);
    var person2 = new fans("lisi",19);
    /*现在的构造函数*/
    function fans(username,age){
        //这里的this指代当前函数实例化的对象
        this.username = username,
        this.age = age;
    }
    fans.prototype.sayHi = function(){
        console.log(this.username);
    }
    var person1 = new fans("zhangsan",20);
    var person2 = new fans("lisi",19);
    console.log(person1.__proto.__ == fans.protortpe);
```

### 13.3.2、对象属性的增删该查

```javascript
var obj = {};
obj.x = 2;//直接添加属性
console.log(obj.x);//通过.访问属性
obj.x = 5;//设置属性
console.log(obj["x"]);//通过[]访问属性
delete obj.x;//删除属性
console.log(obj.x);

//思考obj3 和 obj4 内容是什么？为什么？
var obj3 = {};
for(var i=0;i<10;i++){
    obj3.i = i;
}

var obj4 = {};
for(var i=0;i<10;i++){
    obj4[i] = i;
}
```

# 14、JS对象属性特性

## 14.1、对象属性特性简介

```javascript
var objProto = {
    z:3
};
var obj = Object.create(objProto);
obj.x = 1;
obj.y = 2;
console.log(obj.x);//1
console.log(obj.y);//2
console.log(obj.z);//3

console.log(obj.__proto__)
//原型链上有toString属性
console.log(obj.toString);
//对象上的某些属性和方法是没有办法遍历出来的
//用for in 来遍历所有原型链上的属性
for(var k in obj){
    console.log(k,obj[k]);
}
//x:1,y:2,z:3
```

## 14.2、对象属性（数据属性）特性

### 14.2.1、对象属性特性及其设置

使用defineProperty方法设置

Object.defineProperty(obj,x,{});

| 特性         | 含义                           |
| ------------ | ------------------------------ |
| value        | 对应的属性值                   |
| writable     | 确定是否可写                   |
| configurable | 确定属性是否能删除，是否可配置 |
| enumerable   | 确定是否可枚举                 |

```javascript
var obj = {
    x:1
}
Object.defineProperty(obj,"x",{
    //是否可修改，name属性是不可修改的
    writable:false,
    //是否可配置，定义的属性能否被删除
    configurable:false,
    //是否可枚举，定义属性能否被遍历到
    enumerable:true,
    //定义属性值
    value:'hhh'
});
for(var k in obj){
    console.log(k,obj[k]);
}
```

### 14.2.2、对象添加属性

## 14.3、对象访问器属性的特性

## 14.4、特性描述符及补充

# 15、JS原型继承

## 15.1、JS对象及继承方式综述

## 15.2、JS对象的原型链

## 15.3、基于构造函数实现的原型继承

# 16、JS中的this

## 16.1、JS this简介及特点

## 16.2、JS this四种应用场景

## 16.3、JS this缺陷及解决方法

# 17、深入理解JS的继承方式

## 17.1、JS对象-对象原型继承

## 17.2、通过构造函数模拟类-类的继承

## 17.3、JS继承补充

# 18、Array数组

## 18.1、数组的创建和基本操作

## 18.2、稀疏数组与多维数组

## 18.3、数组的方法和相关高阶数组

# 19、Date日期

## 19.1、Date简介及创建Date对象

## 19.2、Date方法（静态方法、原型方法）

## 19.3、日期和时间格式

# 20、RegExp正则表达式

## 20.1、正则表达式简介及正则对象

## 20.2、RegExp及String相关的正则方法

## 20.3、正则表达式应用案例

# 21、Error及异常处理

## 21.1、JS异常处理

## 21.2、Error对象及其子对象

# 22、Math对象

# 23、JSON对象

## 23.1、JSON简介

## 23.2、JSON对象方法

## 23.3、JSON案例

# 24、jQuery核心

## 24.1、jQuery简介

## 24.2、jQuery选择器

## 24.3、jQuery时间

## 24.4、jQuery DOM操作

#  25、JS事件及事件流

## 25.1、JS事件及事件对象

## 25.2、JS事件响应

## 25.3、JS事件流（冒泡、捕获）

# 26、JS异步与网络数据交互

## 26.1、JS异步相关概念

## 26.2、JS异步的几种形式

## 26.3、JS异步与数据交互

# 27、ES6中的let和count

## 27.1、ES5中的var及其缺陷

## 27.2、ES6中的let与const

## 27.3、let与const的重要特性

# 28、ES6中变量的解构赋值

## 28.1、数组的解构赋值

```javascript
//先进行解构解析在进行赋值
var [a,b,c]=[1,2,3];
console.log(a,b,c);//1 2 3

//let 也支持解构赋值
let [foo,[[bar],baz]]=[1,[[2],3]];
console.log(foo,bar,baz);//1 2 3
/*
	...变量表示剩余的所有，其他元素匹配完成后剩余的元素
*/
let [head,...tail]=[1,2,3,4];
console.log(head,tail);//1 [2,3,4]
/*
	左侧元素多余右侧元素
	未匹配到的变量为undefined
	...跟的变量未匹配到的元素为[空数组]
*/
let [d,e,...f] = ['a'];
console.log(d,e,f);//a undefined []

var [doo2] = [];
var [bar,fee2]=[1];
console.log(doo2,fee2);//undefined undefined
/*嵌套情况也是先解析在进行匹配*/
let [a2,[b2],d2]=[1,[2,3],4];
console.log(a2,b2,d2);//1  2 4

//？？？？？？？？？？？？？？？？？
let a = [];
let b = [2,3,4];
[a[0],a[1],a[2]]=b;
console.log(a==b);//false
console.log(a);//2 3 4

let a = [];
let b=[2,3,4];
a = b;
console.log(a == b);//true
```

## 28.2、对象的解构赋值

```javascript
//对象的解构与数组有一个重要的不同
/**
 * 数组的元素是按次序排列的，变量的取值由它的位置决定
 * 而对象的属性没有次序，变量必须与属性同名，才能取到正确的值
 */
var {bar2,foo2}={foo2:"hh",bar2:"kk"};
console.log(foo2,bar2);

var {baz3} = {foo3:"lll",bar3:"ggg"};
console.log(baz3);//undefined

//左为键值对时，注意键值对赋值时的对应关系
var {foo4:baz4} = {foo4:"aaa",baz4:"bbb"};
console.log(baz4);//aaa

let obj1 = {first:'hello',last:'world'};
let {first:f,last:l} = obj1;
console.log(f,l); //hello world
//两种写法不一样但是结果一样
let{first,last} = obj1;
console.log(first,last);//hello world

//这实际上说明：对象的解构赋值的是下面形式的简写
var {foo5:foo5,bar5:bar5} = {foo5:"ddd",bar5:"kkk"};
//也就是说：对象的解构赋值的内部机制，是先找到同名属性，
//然后再付给对应的变量。真正被赋值的是后者而不是前者
var {foo6:bcd} = {foo6:"his",bcd:"kdjo"};
console.log(bcd);//"his"
console.log(foo6);//报错 foo6 is not a defined
//也就是被赋值的是bcd而不是foo6

//对象的解构也可以指定默认值。
var {x2 = 3} = {};
console.log(x2); // 3

var {x3, y3 = 5} = {x3: 1};
console.log(x3); // 1
console.log(y3); // 5
```

## 28.3、字符串的解构赋值

```javascript
//类似数组的对象都有一个length属性，因此还可以对这个属性解构赋值
let {length:len} = 'hello';
console.log(len);//5

//解构赋值的时候，如果等号右边是数值和布尔值，则会先转为对象。
let {toString:s1} = 123;
console.log(s1);//ƒ toString() { [native code] }

let {toString:s2} = true;
console.log(s2);//ƒ toString() { [native code] }

//数值和布尔值的包装对象都具有toString属性，因此变量s都能取到值
//解构赋值的规则是，只要等号右边不是对象，就先将其转换为对象在进行解构赋值
//由于undefined和null无法转换为对象，所以对他们进行解构赋值，都会报错

let {prop:x}=undefined;
let {prop:y} = null;
```

## 28.4、函数的解构赋值

```javascript
function add([x,y]){
    return x+y;
}
add([1,2]);//3

[[1,2],[3,4]].map(function([a,b]){return a+b;})
// [3,7] ===>1+2 3+4

//函数参数的解构也可以使用默认值，
function move1({x=0,y=0}={}){
    return [x,y];
}
console.log(mov1({x:3,y:4}));//[3,4]
console.log(move1({x: 3})); // [3, 0]
console.log(move1({})); // [0, 0]
console.log(move1()); // [0, 0]

//注意，下面的写法会得到不一样的结果。
function move2({x, y} = { x: 0, y: 0 }) {
    return [x, y];
}
console.log(move2({x: 3, y: 8})); // [3, 8]
console.log(move2({x: 3})); // [3, undefined]
console.log(move2({})); // [undefined, undefined]
console.log(move2()); // [0, 0]
//上述代码是函数move2的参数指定默认值，而不是为变量x和y指定默认值，所以会得到与之前不一样的的结果

//undefined就会触发函数参数的默认值
```



# 29、ES6对内置对象的扩展

## 29.1、ES6对String和RegExp的扩展

1.对String的扩展

```javascript
//ES6提供了字符串的遍历接口（for...of循环遍历）
for(let x of "foo"){
    console.log(x);
}// f o o
/*
	startsWith():以什么开始
	endsWith():以什么结尾
	includes():包含什么
*/
//提供新的方法用于查找、判断和生成字符串
var s = "Hello World!";
s.startsWith("Hello");//true
s.endsWith("!");//true
s.includes("o");//true
//第二个参数，表示开始搜索的位置
s.startsWith('world', 6); // true
s.endsWith('Hello', 5); // true
s.includes('Hello', 6); // false

/*
	repeat方法返回一个新的字符串，将原字符串重复n次
	如果参数是小数会被取整
	如果参数是负数或者是Infinity，会报错
*/
'x'.repeat(3);//'xxx'
'nihao'.repeat(2.5);//'nihaonihao'
'hh'.repeat(-1);//RangeError
'na'.repeat(Infinity);
```

2.对RegExp的扩展

```javascript
//在ES5中，RegExp构造函数有两种
//1、第一个参数是字符串，第二个参数是正则表达式的修饰符
var reg1 = new RegExp('xyz','i');
//=====>等价于
var reg1 = /xyz/i;

//2、参数是一个正则表达式，这时返回一个原有正则表达式的拷贝
var reg1 = new RegExp(/exy/i);
//=====>等价于
var reg1 = /exy/i;
//这种情况ES5不允许加修饰符，会报错
var reg1 = new RegExp(/xyz/,'i');

//ES6改变了这个行为。
//如果RegExp构造函数第一个参数是正则对象，那么第二个参数可以指定修饰符
//而且，返回正则表达式会忽略原来的修饰符,并用flags返回修饰符
    /* 正则表达式对象.flags获取到正则表达式修饰符 */
new RegExp(/xyz/ig,'i').flags;//'i'

//粘连sticky修饰符
/* sticky y修饰符 他会从上一次匹配成功的结束位置开始匹配*/
var s = 'aaa_aa_a';
var r1 = /a+/g;
var r2 = /a+/y;
r1.exec(s); // ["aaa"]
r2.exec(s); // ["aaa"]
r1.exec(s); // ["aa"]
r2.exec(s); // null
//g修饰符匹配没有位置要求，但是y必须从头开始

// ES5的source属性
// 返回正则表达式的正文
/abc/ig.source
// "abc"
```

## 29.2、ES6对Number和Math的扩展

##  29.3、ES6对Array和Object的扩展

# 30、ES6对函数的扩展

## 30.1、ES6新增的箭头函数

## 30.2、ES6 对函数参数默认值的扩展

## 30.3、ES6中Reat与Spread操作符

# 31、ES6新增数据类型和数据结构

## 31.1、新增数据类型（Symbol）

## 31.2、新增数据结构（Set）

## 31.3新增数据结构（Map）

# 32、Class综述

## 32.1、ES6Class基本预防

## 32.2、ES6Class静态方法、静态属性

## 32.3、ES6 Class的继承

# 33、Promise与异步编程

## 33.1、Promise概念与语法

## 33.2、Promise 原型方法及静态方法

## 33.3、Promise综合案列

# 34、ES6补充部分

## 34.1、ES6迭代器与生成器

## 34.2、ES6模块化开发