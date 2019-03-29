一、HTML5简介

## 1.1、web标准

- 结构标准：HTML；样式标准：CSS；行为标准：W3C DOM、ECMAScript

## 1.2、设计理念

- 避免不必要的复杂性
- 支持已有的内容 
- 求真务实
- 优雅降级

## 1.3、HTML5的优点

- 提升用户体验，加强视觉感受
- 多设备、跨平台支持
- 开放的网络标准

# 二、HTML标签及特性
## 2.1、HTML5标签特性

- H5的新标签分类
  - 优化文档结构，结构性元素
  - 提供新的功能，功能性元素

## 2.2、HTML5新增的结构性元素

### 2.2.1新增的结构元素

​	HTML5定义了一组新的**语义化标签**来描述元素的内容；语义化标签能简化HTML网页设计，并且让机器可以更好地理解网页，以促进信息的共享和传播。

#### （1）header元素
​	 header元素是一种具有**引导和导航作用**的结构元素，通常用来放置**整个页面  或页面**内的**一个区块的标题、搜索表单、logo**等。

​	一个**网页内**不限制只能有一个header元素，**可以拥有多个**，可以为每个内容区域块添加header元素。

#### （2）nav元素

​	nav元素**定义页面导航的链接组**，其中的导航元素链接到其他页面或当前页面的其他部分。

​	网页可以拥有多个nav元素，作为页面整体或不同部分的导航。并不是把所有的链接都有放进nav元素，如果文档中有“前后”按钮，则应该把他放到nav元素中。

#### （3）article元素

​	article元素定义**可以独立被外部引用的内容**。可以是一篇博客、一段评论......

​	一个article元素通常有自己的标题和脚注。

#### （4）section元素

​	section元素**定义文档中的区域**，比如章节、页眉、页脚或文档中的其他部分。

#### （5）aside元素
​	aside元素用来表示当前页面或文章的**附属信息**
​	①**包含在article元素中**，作为主要内容的附加信息部分，内容可以是与当前文章有关的相关资料、名次解释等。

​	②**在article元素之外**，作为页面或站点全局的附属信息。最典型的是侧边栏，内容包括友情链接，博客中的文章列表、广告

#### （6）footer元素

​	footer元素**定义页脚**。通常包括其相关区块的脚注信息，如作者、文档的创造日期以及版权信息等。

​	一个页面中不限制只可以用一个footer元素。可以为article元素或section元素天界footer。

## 2.3、HTML5新增的功能性

### 2.3.1、新增的功能元素

#### （1）video播放视频，audio播放音频

- 属性

  | 属性     | 功能                              |
  | -------- | --------------------------------- |
  | src      | 指定音/视频文件的URL地址          |
  | controls | 是否添加浏览器自带的播放控制条    |
  | loop     | 是否循环播放音频、视频            |
  | autoplay | 指定媒体是否在页面加载后自动播放  |
  | width    | 指定视频的宽度，只有video标签具有 |
  | height   | 指定视频高度，只有video标签具有   |

#### （2）embed

​	定义嵌入的内容，比如插件

 - 属性：

   | 属性   | 值   | 描述                     |
   | ------ | ---- | ------------------------ |
   | src    | url  | 嵌入内容的 URL。必选属性 |
   | type   | type | 定义嵌入内容的类型       |
   | width  | px   | 设置宽度                 |
   | height | px   | 设置高度                 |

#### （3）time

   ​	定义公历时间（24小时制）或日期

该元素能够以机器可读的方式对日期和时间进行编码，搜索引擎也能够生成更智能的搜索结果。

####  （4）details

   ​	标签用于描述文档或文档某个部分的细节。（demo2-5）

与 <summary>标签配合使用可以为details定义标题。标题是可见的，用户点击标题时，会显示出details。	

```html
<details>
	<summary> Copyright 2018.</summary>
	<p>版权归H5方向所有</p>
</details>
```

####  （5）mark

   ​	标签定义带有记号的文本

```html
<p>每天都要吃<mark>早餐</mark></p>
```

####  （6）progress

   ​	标签标示任务的进度（进程）

| 属性  | 值     |                      |
| ----- | ------ | -------------------- |
| max   | number | 规定一共需要多少工作 |
| value | number | 规定已经完成多少任务 |



### 2.3.2、插入音频、视频示例

```html
<audio src="02.ogg" controls="controls">
您的浏览器不支持Audio
</audio>

<video src="1.ogg" controls="controls">
您的浏览器不支持Video标签
</video>
```



###   2.3.3、音/视频格式兼容性解决方案(source)

- **audio/video组合source元素**

  可以链接不同的音频文件，也可以为同一个每天数据指定多个播放格式。

  浏览器将使用第一个可识别的格式。

  ```html
  <audio controls="controls">
      <source src="2.ogg" type="audio/ogg">
      <source src="2.mp3" type="audio/mpeg">
      您的浏览器不支持Audio
  </audio>
  
  <video width="320" height="240" controls="controls">
      <source src="moive.ogg" type="viseo/ogg">
      <source src="movie.mp4" type="video/mp4">
      您的浏览器不支持Video
  </video>
  ```

### 2.3.4、更灵活的音/视频操作

​	通过JavaScript API可以更灵活的控制音/视频，并实现更丰富的功能

常用的控制函数

| 方法    | 动作                         |
| ------- | ---------------------------- |
| play()  | 加载音频、视频               |
| pause() | 暂停处于播放状态的音频、视频 |
| load()  | 重新加载音频、视频元素       |

### 2.3.5、音乐播放器

​	通过play()、pause() 、currentTime实现对音频的播放、暂停、快进操作

## 2.4、废除的元素

### 2.4.1、表现性元素

- 删除big,center,font,s,u等
- h5中提倡把呈现性的功能放在css样式表中统一编辑

### 2.4.2、框架类元素

- 删除frameset、frame、noframes标签，只支持iframe框架

### 2.4.3、只有部分浏览器支持的元素

- 删除blink，bgsound等

# 三、表单

## 3.1、新增input输入类型

### 3.1.1数值输入文本框-number

```html
<input type="number" name="demoNum" min="1" max="100" step="2">
```

​	注：外观与text文本框相同，但不能输入数值以外的文字，否则提交时将内容作为空白进行提交。

### 3.1.2、邮箱输入文本框-email

​	注：专门用来输入email地址。当表单提交时，会自动校验是否符合邮箱的正则表达式，但不检验该email地址是否存在。

​	placeholder属性为提示信息。

### 3.1.3、url输入文本框-url

​	注：专门用来输入url地址。当表单在提交前，会自动校验是否符合url网址的规范。

### 3.1.4、电话号码输入文本框-tel

​	注：手机中 的浏览器遇到tel类型的input元素时，会自动变触摸屏幕键盘以方便用户输入。

### 3.1.5、滑动条文本框-range

```html
<input type="range" min="0" max="50" step="5" name="redom" value = "0"/>
```

​	注：用于应该包含一定范围内数字值的输入域。range类型显示为滑动条。能够设定对所接受的数字的限定。

### 3.1.6、日期时间输入文本框-date

​	注：date类型的input元素以日历的形式方便用户输入。还有其他的**type：time、datetime-local、month、week、datetime**

### 3.1.7、颜色选择文本框-color

​	注：color类型的input元素用来选取颜色，其提供了一个颜色选择器

### 3.1.8、搜索功能文本框-search

​	注：search类型用于搜索域，比如站点搜索或Google搜索

## 3.2、新增表单元素

### 3.2.1、datalist元素

​	datalist元素—为输入框提高可选的列表

一般和<input>标签配合使用，来设置<input>可能的值。把datalist绑定到输入域，需要将输入域list属性引用datalist的ID。列表通过datalist中的option元素创建。如不从列表中选择某项，也可自行输入其他内容。每个option元素必须设置value属性。

```html
<form action="" method="get">
    <!-- id值要和input中list的值相同才能关联 -->
		exo中的成员：
    <input type="search" name="sousuo" list="member">
		<datalist id="member">
			<select>
				<option >xiumin</option>
				<option >sohu</option>
				<option >lay</option>
				<option >bakeyuab</option>
				<option> chen</option>
				<option >pcy</option>
				<option> D.O.</option>
				<option >kai</option>
				<option >sehun</option>
			</select>
		</datalist>
	</form>
```

### 3.2.2、output元素

​	output元素用于在浏览器中显示计算结果或脚本输出。

```html
<form oninput="x.value=parseInt(a.value)+parseInt(b.value)">
		0<input type="range" id="a" value="50">100
		<!-- 这是个滑竿 -->
		+<input type="number" id="b" value="50">
		=<output name="x" for="a b"></output>
</form>
```

| 属性 | 值                    | 描述                             |
| ---- | --------------------- | -------------------------------- |
| for  | ID of another element | 定义输出域相关的一个或多个元素   |
| form | form name             | 定义输入字段所属的一个或多个表单 |
| name | unique name           | 定义对象的唯一名称               |

## 3.3、新增表单属性

### 3.3.1、form属性

​	form属性规定输入域所属的一个或多个表单，属性值为所属表单是id

​	可将表单内的从属元素写在页面的任意位置，然后为该元素指定form属性。如需引用多个表单，使用空格分隔的列表。

```html
<!-- 其他表单的form属性与form元素的ID相等即可相互联系，提交到相同的后台 -->
	<!-- action用于表示提交的后台 -->
	<form id="testform" method="get" action="">
		<!-- required属性用于校验是否填写东西 -->
		姓&nbsp;&nbsp;名：<input type="text" name="name1" 
		autofocus="autofocus" required placeholder="请输入姓名"/>
		<input type="submit" value="提交"/>
	</form>
    <br/>
        自我介绍：<textarea name="textarea1" form="testform"></textarea>
```

### 3.3.2formaction、formmethod属性

​	formaction：实现将表单提交到不同的页面

​	formmethod：对每个表单元素分别指定不同的提交方法

### 3.3.3、required、placeholder属性

​	required属性：布尔属性，规定输入域在提交之前必须填写

​	placeholder属性：没有值时出现在文本框中的字符串，获取焦点输入框提示信息消失，以柔和的灰色文本显示在域中。

### 3.3.4、list属性

​	input元素的list属性与datalist元素的ID属性绑定，提供列表输入选项。

### 3.3.5、autofocus、multiple

​	autofocus属性：布尔属性，页面加载时表单域自动聚焦；一个页面此属性仅可设置一次

​	multiple属性：用于文件上传控制，设置此属性后，允许上传多个文件。

​	max/min/step属性：设置最大/小值/数值或日期时间的增量。

​	

# 4、地理位置定位

## 4.1、HTML5获取当前地理位置

4.1.1、getCurrentPosition(onSuccess,onError,options)



## 4.2、地理位置定位示例

# 5、离线应用

## 5.1、创建离线应用

5.1.1、创建缓存清单文件（manifest文件）

​	文件扩展名：appcashe

​	manifest 文件需要在web服务器上配置正确的 MIME 类型为:  

text/cache-manifest。(主要用于告诉浏览器打开方式)

​	（MIME: 多用途互联网邮件扩展类型，是设定某种扩展名的文件用一种应程序来打开的方式类型）

5.1.2、在html标记中指定使用缓存文件

5.2、JavaScript接口

# 6、web存储

## 6.1、存储简介

​	Cookie：保存用户信息、用户设置、密码记忆

## 6.2、LocalStorage

​	将数据保存在客户端本地的硬件设备中，即使浏览器被关闭了，该数据仍然存在，**下次打开浏览器访问网站仍然可以继续使用。**

​	localStorage为永久保存

数据组织形式：

- ​	存储是基于键/值对的形式存储，每个键值对称为一个项。存储和检索数据都是通过制定的键名。
- ​        键名的类型是字符串类型
- 值可以包括字符串、布尔值、数值在内的任意JavaScript类型

```javascript
//1、检查浏览器是否支持
if(!window.localStorage){
	alert("您浏览器不支持localStorage！");
}else{
	//主逻辑业务
}
```

浏览器提供localStorage对象的操作：

- 存储数据项：
  - localStorage.setItem(key,value)
  - localStorage["key"] = value
  - localStorage.key = value
- 读取数据项
  - localStorage.getItem(key)
  - localStorage["key"]
  - localStorage.key
- 清除数据项
  - localStorage.removeItem(key)
- 清除全部数据
  - localStorage.clear()
- 获得键名
  - localStorage.key(index)
- 获得数据项的个数
  - localStorage.length

存储数据的数据类型：

​	仅能存储字符串类型的数据；对象转换为字符串（JSON API ---JSON.stringify()转换成字符串，JSON.parse()转换成对象）

## 6.3、Session Storage

​	将数据保存在session对象中。session是指用户在浏览某个网站时，从进入网站到浏览器关闭所经过的这段时间。session对象可以用来保存在这段时间内所要保存的任何数据。**当用户关闭浏览器窗口后，数据会被删除。**

​	sessionStorage为临时保存

sessionStorage对象方法

- 保存数据：sessionStorage.setItem(key,value)
- 读取数据：sessionStorage.getItem(key)
- 获得键名：sessionStorage.key(index)
- 移除数据：sessionStorage.removeItem(key)
- 清除所有数据：sessionStorage.clear()

## 6.4、网页访问计数器

​	localStorage可以作为web应用访问计数器

​	sessionStorage可以作为会话计数器

# 7、数据通信

## 7.1、数据通信

​	Web应用需要从服务器获取页面或数据，也需要和其他用户进行数据交换。这些都是Web中的数据通信。

​	HTTP协议的缺陷：通信只能由客户端发起，服务器总是被动的

​	Ajax轮询与长轮询的原理：

ajax轮询：即让浏览器隔几秒就发送一次请求，询问服务器是否有新信息。

长轮询：采取的是阻塞模型，即客户端发起连接后，如果没消息，就一直不返回Response给客户端，直到有消息才返回。返回完之后，客户端再次建立连接，周而复始。

## 7.2、WebSocket

​	WebSocket是HTML5提供的一种浏览器与服务器进行**全双工**通讯的**网络通讯协议。**

​	特点：

（1）建立在 TCP 协议之上，服务器端的实现比较容易。

（2）与 HTTP 协议有着良好的兼容性。默认端口也是80和443，握手阶段采用 HTTP 协议，不容易屏蔽，能通过各种 HTTP 代理服务器。

（3）数据格式比较轻量，性能开销小，通信高效。

（4）可以发送文本，也可以发送二进制数据。

（5）没有同源限制，客户端可以与任意服务器通信。

（6）协议标识符是ws（如果加密，则为wss），服务器网址就是 URL。

## 7.3、WebSocket客户端

7.3.1、WebSocket构造函数

```javascript
var Socket  = new WebSocket(url,[protocol])
//url:第一个参数指定连接的URL
//protocol：第二个参数可选，指定了可接受的子协议
var Socket = new WebSocket('ws://localhost:8080');
```

7.3.2、WebSocket属性

| 属性                     | 描述                                                         |
| ------------------------ | ------------------------------------------------------------ |
| WebSocket.ready.State    | 返回实例对象的当前状态，共4种。                       connecting：值为0，表示正在连接                 open：值为1，表示连接成功，可以通信了closing：值为2，表示连接正在关闭               closed：值为3，表示连接已经关闭，或者打开连接失败。 |
| WebSocket.bufferedAmount | 表示已被 send()放入正在队列中等待传输，但是还没有发出二进制数据。 |

```javascript
switch (ws.readyState) {
      case WebSocket.CONNECTING:
        // do something
        break;
      case WebSocket.OPEN:
        // do something
        break;
      case WebSocket.CLOSING:
        // do something
        break;
      case WebSocket.CLOSED:
        // do something
        break;
      default:
        // this never happens
        break;
}
//实例对象的bufferedAmount属性可以用来判断发送是否结束
 var socket = new WebSocket(url, [protocol] );
 var data = new ArrayBuffer(10000000);
 socket.send(data);
 if (socket.bufferedAmount === 0) {
      // 发送完毕
 } 
 else {
      // 发送还没结束
 }
```

7.3.3、WebSocket事件

| 事件    | 事件处理程序        | 描述                       |
| ------- | ------------------- | -------------------------- |
| open    | WebSocket.onopen    | 连接建立时触发             |
| message | WebSocket.onmessage | 客户端接收服务端数据时触发 |
| error   | WebSoc.onerror      | 通信发生错误时触发         |
| close   | WebSocket.onclose   | 连接关闭时触发             |

​	window.WebSocket.onopen

实例对象的onopen属性，用于指定连接成功后的回调函数。

​	window.WebSocket.onmessage

实例对象的onmessage属性，用于指定收到服务器数据后的回调函数。

​	window.WebSocket.onclose

实例对象的onclose属性，用于指定连接关闭后的回调函数。

7.3.4、WebSocket方法

| 方法              | 描述             |
| ----------------- | ---------------- |
| WebSocket.send()  | 使用连接发送数据 |
| WebSocket.close() | 关闭连接         |

​	window.WebSocket.send()

实例对象的send()方法用于向服务器发送数据。

​	window.WebSocket.close()

实例对象的close()方法用于关闭连接。

demo7-1.html

![1553516382985](D:\大二下\base_nodes\%5CUsers%5Clenovo%5CAppData%5CRoaming%5CTypora%5Ctypora-user-images%5C1553516382985.png)

## 7.4、WebSocket服务端

常用的Node实现以下三种：

​	WebSockets；Socket.IO；WebSocket-Node

使用WebSocket

​	基于WebSocket实现用户和用户聊天

​	提示：

​	•在WebSocket服务器端，每个用户连接之后都创建一个connection对象。使用该对象向此用户发送数据。

​	•要传输包含几项内容的数据时，可以使用JSON进行传输（JSON和字符串可以互相转换）

# 8、文件

## 8.1、file对象与filelist对象

​	file对象：指用户选择的文件

​	FileList对象：指用户选择的文件列表。

​	每个文件都是file对象，FileList对象是file对象的列表，代表用户选择的所有文件。

| 属性             | 描述                                                 |
| ---------------- | ---------------------------------------------------- |
| name             | 文件名，该属性只读                                   |
| size             | 文件的大小，单位为字节，该属性只读                   |
| type             | 文件的MIME类型，如果分辨不出类型，则为空字符串，只读 |
| lastModified     | 文件的上次修改时间，格式为时间戳                     |
| lastModifiedDate | 文件的上次修改时间，格式为Date对象实例。             |

```html
<body>
//所有type属性为file的<input>元素都有一个files属性，用来存储用户所选择的文件。files 属性值就是 FileList 对象。
//files有length属性和item方法。可以通过files[index]或者files.item(index)获取选择的file对象。
//实例：使用FileList对象与file对象
	<script>
		function ShowFileName(){
			var file;
			var file1;
			file1 = document.getElementById("file");
			console.log(file1.files);
			for(var i=0; i<file1.files.length; i++){
				file = file1.files[i];
				console.log(file);
			}
		}
	</script>
	<input type="file" id="file" multiple/>
	<input type="button" value="文件上传" onclick="ShowFileName();"/>
</body>
```

## 8.2、Blob对象

file对象继承了Blob对象

Blob对象（binary large object 二进制大对象），表示二进制原始数据。

| 属性      | 描述                                                   |
| --------- | ------------------------------------------------------ |
| slice（） | 可以访问到字节内部的原始数据块                         |
| size      | 表示一个Blob对象的字节长度                             |
| type      | 表示Blob的MIME类型，如果是未知类型，则返回一个空字符串 |

通过类型过滤文件：

```html
//实例：通过类型过滤图片文件
<script>
	function FileUpload(){
	    var file;
	    for(var i=0;i<document.getElementById("file").files.length;i++)
	    {
	        file = document.getElementById("file").files[i];
	        if(!/image\/\w+/.test(file.type)){
	            alert(file.name+"不是图像文件！");
	            break;            
	        }
	        else{
	            //此处可加入文件上传的代码
	            alert(file.name+"文件已上传");
	        }
	    }
	}
</script>
<body>
	选择文件：
	<input type="file" id="file" multiple/>
	<input type="button" value="文件上传" onclick="FileUpload();"/>
</body>
```



## 8.3、FileReader对象

FileReader对象：用来把文件读入内存，并读取文件中的数据

```html
//检查浏览器是否支持FileReader对象
     // if ( typeof FileReader == 'undefined' ) 
     if ( ! window.FileReader )
	  {           
		alert( " 您的浏览器未实现 FileReader 接口 " ); 
	  } 
     else 
	  {                  
		var reader = new FileReader();   
	  } 
```

8.3.1、FileReader方法

​	**FileReader无论读取成功或失败，不返回结果，只存储在FileReader的result属性中。**

| 方法名             | 参数            | 描述                                                         |
| ------------------ | --------------- | ------------------------------------------------------------ |
| abort              | none            | 中断读取                                                     |
| readAsBinaryString | file            | 将文件读取为二进制字符串。通常将它传送到服务器端以存储文件   |
| readAsDataURL      | file            | 将文件读取为DataURL。读取内容可以作为URL属性，即可以将一个图片的结果指向给一个img的src属性。 |
| readAsText         | file,[encoding] | 将文件读取为文本数据。第一个参数传入Blog对象，第二个参数传入编码格式。 |

8.3.2、FileReader对象的事件

​	当FileReader对象读取文件时，会伴随着一系列事件，它们表示读取文件时不同的读取状态。

| 事件        | 描述                         |
| ----------- | ---------------------------- |
| onabort     | 数据读取中断时触发           |
| onerror     | 数据读取出错时触发           |
| onloadstart | 读取开始时触发               |
| onprogress  | 读取中                       |
| onload      | 文件读取成功完成时触发       |
| onloadend   | 读取完成触发，无论成功或失败 |

​	实现文本文件的读取

使用 FileReader 对象的 readAsText()方法实现文本文件的预览。

需要注意：txt文件的编码格式需要设置为UTF-8。

# 9、拖放

## 9.1、DataTransfer对象

1. setData（format,data） --向DataTransfer对象存入数据

   ev.dataTransfer.setData("text", ev.target.innerHTML);

2. getData（format） --从DataTransfer对象读数据

   ev.dataTransfer.getData("text");

3. 现在支持拖动的MIME的类型有：

4. 属性：

| 属性          | 描述                         |
| ------------- | ---------------------------- |
| files         | 拖拽文件列表                 |
| dropEffect    | 拖放操作的视觉效果           |
| types         | 存入数据的种类               |
| effectAllowed | 指定拖放操作所允许的一个效果 |

## 9.2、实现拖放的步骤

（1）将需要拖放的对象元素的draggable属性设为true，即draggable ='true'

（2）编写与拖放有关的事件处理代码

​	拖放相关的事件

| 拖动生命周期 | 事件 | 描述 | 产生事件的元素 |
| ------------ | ---- | ---- | -------------- |
|              |      |      |                |
|              |      |      |                |
|              |      |      |                |
|              |      |      |                |
|              |      |      |                |
|              |      |      |                |
|              |      |      |                |



















