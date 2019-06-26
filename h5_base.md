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

# 4、地理位置定位

## 4.1、Geolocation API

**HTML5 GeolocationAPI不指定设备使用哪种底层技术来定位使用应用程序的用户，它只是用于检索位置信息的API**

geolocation 对象，此对象为navigator对象的一个属性

**Geolocation API 存在于navigator对象中，包含 3 个方法：**

**（1）getCurrentPosition(onSuccess, onError,options)    //获取当前地理位置**

参数1：获取数据成功后执行的回调函数，使用 Position 对象作为唯一的参数

参数2（可选）：获取数据失败时执行的回调函数，使用 PositionError 对象作为唯一的参数

参数3 （可选）：可选参数列表，可通过该对象参数设定最长可接受的定位返回时间、等待请求的时间和是否获取高精度定位

**（2）watchPosition(onSuccess, onError,options)     //持续监视当前地理位置**

监测用户位置，位置发生改变时即调用成功回调函数

**（3）clearWatch()                    //清除监视**

该方法会返回一个 ID，如要取消监听可以通过  clearWatch(watchId) 传入该 ID 实现取消的目的。

## 4.2、HTML5获取当前地理位置



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

```javascript
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

## 9.1、拖放

1. **源对象**：值鼠标点击一个事物，可以是图片，DIV，一段文本等等
2. **目标对象**：值拖动源对象后移动到一块区域，源对象可以进入到这个区域，可以在这个区域上方悬停（未松手），可以松手释放将源对象放置此处（已松手），也可以悬停后离开该区域。

## 9.2、DataTransfer对象

1. **DataTransfer**：拖拽数据传递对象，为**事件对象的一个属性**，用于在源对象和目标对象的事件间传递字符串格式的数据。（保存被拖动的数据）

2. **事件对象**：在触发DOM上的某个事件时，会产生一个事件对象Event。事件对象包含所有与事件相关的信息。包括导致事件的元素、事件的类型、键盘按键状态、鼠标的位置等。在事件处理函数执行时，事件对象会由浏览器自动传递给事件处理函数。事件处理函数中，声明形参接收该参数。**preventDefault（）取消事件的默认动作。**

3. **DataTransfer对象的方法：**

   setData（format,data） --向DataTransfer对象存入数据

   ​	ev.dataTransfer.setData("text", ev.target.innerHTML);

   getData（format） --从DataTransfer对象读数据

   ​	ev.dataTransfer.getData("text");

4. 现在支持拖动的MIME的类型有：

   “text/plain（文本文字）”、“text/html”、“text/xml”、“text/url-list（URL列表，每个URL为一行）”

5. **DataTransfer对象的属性**：

| 属性          | 描述                                                         |
| ------------- | ------------------------------------------------------------ |
| files         | 拖拽文件列表                                                 |
| dropEffect    | 拖放操作的视觉效果（在PC Web端主要是鼠标手型上，值为copy，link，move或none） |
| types         | 存入数据的种类                                               |
| effectAllowed | 指定拖放操作所允许的一个效果                                 |

## 9.3、实现拖放的步骤

（1）将需要拖放的对象元素的draggable属性设为true，即draggable ='true'

​	注：img元素和a元素默认允许拖放

（2）编写与拖放有关的事件处理代码

​	**拖放相关的事件**

| 拖动生命周期 | 事件      | 描述         | 产生事件的元素           |
| ------------ | --------- | ------------ | ------------------------ |
| 拖动开始     | dragstart | 开始拖拽     | 被拖放的元素             |
| 拖动过程中   | drag      | 拖放过程中   | 被拖放的元素             |
| 拖动过程中   | dragenter | 拖拽进入     | 拖放过程中鼠标经过的元素 |
| 拖动过程中   | dragover  | 拖拽经过     | 拖放过程中鼠标经过的元素 |
| 拖动过程中   | dragleave | 拖拽离开     | 拖放过程中鼠标经过的元素 |
| 拖动结束     | drop      | 拖拽释放     | 目标元素                 |
| 拖动结束     | dragend   | 拖放操作结束 | 目标元素                 |

```javascript
document.addEventListener('dragstart', function (event) {
		console.log('dragstart开始拖拽: ' + event.dataTransfer);	
	});
	document.addEventListener('dragenter', function (event) {
		console.log('dragenter拖拽进入: ' + event.dataTransfer);	
	});
	document.addEventListener('dragleave', function (event) {
		console.log('dragleave拖拽离开: ' + event.dataTransfer);	
	});
	document.addEventListener('dragover', function (event) {
		event.preventDefault();//必须要有，默认
		event.dataTransfer.dropEffect = "copy";
		console.log('dragover拖拽经过: ' + event.dataTransfer);	
	});
	document.addEventListener('drop', function (event) {
		console.log('drop拖拽释放: ' + event.dataTransfer);	
	});
	document.addEventListener('dragend', function (event) {
		console.log('dragend拖放操作结束: ' + event.dataTransfer);	
	});
```

**（3）拖放**

```html
（1）源对象设置元素为可拖放：draggable=“true”
（2）源对象设置拖动什么 ondragstart 和setData（） 
（3）目标对象放置元素到何处 ondragover （默认无法将元素放置到其他元素中。如果需要设置允许放置，必须阻止对元素的默认处理方式）
（4）目标对象进行放置 ondrop 忽和 getData（） 
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<link rel="icon"/>
	<style type="text/css">
		div{
			border:2px solid gray;
			width:180px;
			height:180px;
		}
	</style>
</head>
<body>
	<!-- 3、给目标对象设置可放置属性
		 4、给目标对象绑定结束时的事件处理函数 -->
	<div ondragover="allowDrop(event)" ondrop="drop(event)"></div>
	<!-- 1、在原对象上设置为可拖放
		 2、给原对象设置开始拖放事件 -->
	<img src="images/taidi.jpg" id="dragimg" draggable='true' ondragstart="drag(event)"/>
</body>
<script>
	function drag(ev){
		//这里的target指代原对象
		ev.dataTransfer.setData("Text",ev.target.id);
	}
	function allowDrop(ev){
		ev.preventDefault();
	}
	function drop(ev){
		ev.preventDefault();
		var data = ev.dataTransfer.getData("Text");//获取原对象的id
		ev.target.appendChild(document.getElementById(data));//此时的target指代当前目标对象
		alert("移动成功了！！");
	}
</script>
</html>
```

# 10、画布（一）

## 10.1、创建canvas

​	canvas元素用于绘制图形，只是一块无色透明的图形容器区域。

​	画布是一个空白矩形区域，可以控制其每一像素

```html
   //建议直接设置width和height属性，且不推荐使用px后缀
<canvas id="canvas" width="200" height="200">
	您的浏览器不支持canvas元素，请更换或更新浏览器
</canvas>
```

​	**getContext()方法**

​	使用canvas元素，首先需要调用getContext()方法。

getContext()返回一个对象，提供了用于画布上绘图的方法和属性。context被称为绘图环境对象，包含绘图的上下文环境。

```javascript
var canvas = document.getElementById('canvas');
var context = canvas.getContext('2d');
//该方法可以接受两个值：2d 和 3d，分别表示二维和三维
```

## 10.2、绘制直线、多边形

### 10.2.1、canvas坐标及方法

​	canvas是一个二维网络，坐标原点(0,0)位于canvas的左上角。x轴水平向右延伸，y轴向下延伸。

### 10.2.2、路径和描绘

| 方法        | 含义                                                         |
| ----------- | ------------------------------------------------------------ |
| moveTo(x,y) | 用于创建新的子路径，并规定起始点为（x,y）                    |
| lineTo(x,y) | 为当前子路径添加一条直线。这条直线从当前点开始，到（x,y）结束。当方法返回时，当前点是（x,y） |
| stroke()    | 实际地绘制出通过moveTo()和lineTo()方法定义的路径。默认颜色是黑色的 |

​	**注意：**moveTo(x,y)只是设置起点并不画线。如果没有用moveTo(x,y)规定子路径的起点，则lineTo(x,y)等同于moveTo(x,y)。连完一条线后起点改变，改变为lineTo(x,y)中的坐标。

### 10.2.3、线条样式设置

| 属性        | 含义                               |
| ----------- | ---------------------------------- |
| lineWidth   | 设置当前线条的宽度，默认单位为像素 |
| strokeStyle | 设置绘制描边的颜色                 |

### 10.2.4、填充

| 方法      | 含义                                                         |
| --------- | ------------------------------------------------------------ |
| fill()    | 填充当前绘图（路径）。默认是黑色。如果路径未关闭，那么fill()方法会自动从路径结束点到开始点之间添加一条线，以关闭该路径，然后填充该路径。 |
| fillStyle | 设置用于填充绘画的颜色                                       |

​	注意：建议先填充再描边

### 10.2.5、路径封闭

​	canvas之中只能有一条路径存在，称之为‘’当前路径‘’

| 方法        | 含义                                     |
| ----------- | ---------------------------------------- |
| beginPath() | 开始一条新的路径（路径开始点）           |
| closePath() | 创建从当前点到开始点的路径（路径结束点） |

![1555501689623](D:\大二下\H5程序设计基础\h5_base.md)

## 10.3、绘制弧和圆

arc()方法创建弧/曲线（用于创建圆和部分圆）

context.arc(x,y,r,sAngle,eAngle,anticolckwise)

| 参数          | 描述                                                      |
| ------------- | --------------------------------------------------------- |
| x             | 圆的中心的x坐标                                           |
| y             | 圆的中心的y坐标                                           |
| r             | 圆的半径                                                  |
| sAngle        | 起始角，以弧度计。（0×Math.PI ,0.5×Math.PI，，2×Math.PI） |
| eAngle        | 结束角                                                    |
| anticlockwise | 可选，否则安好逆时针方向绘图。false=顺时针，true=逆时针   |

## 10.4、绘制矩形

context.rect(x,y,width,height)

​	x,y指定矩形左上角的位置

​	width，height指定矩形的尺寸

​	与fill()和stroke（）搭配使用

| 方法                         | 含义                       |
| ---------------------------- | -------------------------- |
| rect(x,y,width,height)       | 创建矩形                   |
| fillRect(x,y,width,height)   | 绘制“已填色”的矩形（实心） |
| strokeRect(x,y,width,height) | 绘制不填色的矩形（空心）   |
| clearRect(x,y,width,height)  | 清空给定矩形内的指定像素   |

## 10.5、透明度 

**globalApha属性**

设置绘图的当前透明值（0-1），可累加

# 11、画布（二）

## 11.1、线条的样式

| 属性       | 描述                                                         |
| ---------- | :----------------------------------------------------------- |
| lineWidth  | 设置当前线条的宽度，以像素计算、                             |
| lineCap    | 设置线条末端线帽的样式                                                                     context.lineCap = "butt \| round \|square"                                                                                   butt              默认。向线条的末端线帽的样式                                  round          向线条的每个末端添加圆形线帽                                    square         向线条的每个末端添加正方形线帽                                   注：round和square会使线条略微变长 |
| lineJoin   | 设置当两条线交汇时所创建边角的类型                                                              context.lineJoin="bevel  \| round  \|  miter"                                          bevel            创建斜角                                                                               round           创建圆角                                                                              miter            默认，创建尖角 |
| miterLimit | 这只最大斜接长度，默认值是10                                                                   斜接长度是指在两条线交汇处内角和外角之间的距离。                  只有在lineJoin=miter时才会有miterLimit |

## 11.2、画布转换和状态保存

​	**画布的转换是指转换画布的坐标系**

### 11.2.1**平移**

**—translate（x,y）** ---坐标系**会累加**

​	平移画布的用户坐标系统，即重新映射画布上的(0,0)的位置

​	x:坐标原点沿水平方向的偏移量

​	y:坐标原点沿垂直方向的偏移量

### 11.2.2、旋转

**—rotate(deg)** ---坐标系**会累加**

​	旋转画布的用户坐标系统，即改变坐标系x与y轴的指向

​	参数angle-----旋转角度，以弧度计（angle=degree/180*Math.PI）

​	正值表示顺时针方向旋转；负值表示逆时针方向旋转

### 11.2.3、缩放

**—scale(sx,sy)-**-----坐标系**会累加**

​	缩放画布的用户坐标系统

​	sx:坐标系x轴缩放的倍数

​	sy:坐标系y轴缩放的倍数

### 11.2.4、save()

​	保存当前canvas绘图环境的所有属性、坐标变换信息等

### 11.2.5、restore()

​	将绘图环境状态恢复为保存值

save()把当前状态的一份拷贝压入到一个保存图像状态的栈中。restore()是出栈。

## 11.3、文字的渲染

| 属性                                  | 描述                                                         |
| ------------------------------------- | ------------------------------------------------------------ |
| fillText(text,x,y,maxWidth)           | 在画布上绘制填色的文本。文本的默认颜色是黑色。                                                                         text      规定在画布上输出的文本                                 x —文本的x坐标位置(相对于画布)      y  —开始绘制文本的y坐标位置                            maxWidth 可选。允许的最大文本宽度，像素 |
| font                                  | 设置画布上文本内容的当前字体属性                          context.font="italic 35px 微软雅黑" |
| strokeText(text,x,y,maxWidth)         | 绘制描边文字。                                                                                     text —规定在画布上输出的文本                                                              x      —开始绘制文本的x坐标位置                                                            y      —开始绘制文本的y坐标位置                                                       maxWidth 可选。允许的最大文本宽度 |
| measureText(text)                     | 返回一个对象，该对象包含以像素计的指定字体宽度               |
| textAlign（center\|end\|left\|right） | 根据锚点，设置文本内容的当前对齐方式（水平对齐）             |
| textBaseline(top\|middle\|bottom)     | 根据锚点，设置在绘制文本时的当前文本基线（垂直对齐）         |

## 11.4、阴影

偏移量可正可负

| 属性          | 描述                                |
| ------------- | ----------------------------------- |
| shadowColor   | 设置用于阴影的颜色                  |
| shadowBlur    | 设置用于阴影的模糊级别              |
| shadowOffsetX | 设置形状与阴影的水平距离，默认值为0 |
| shadowOffsetY | 设置形状与阴影的垂直距离，默认值为0 |

# 12、画布(三)

## 12.1、渐变色

### 12.1.1、线性渐变

线性颜色渐变：从一端到另一端的颜色渐变

**createLinearGradient（x0,y0,x1,y1）**创建线性渐变对象

​	使用该对象作为strokeStyle 或fillStyle属性的值

| 参数  | 描述                |
| ----- | ------------------- |
| x0,y0 | 渐变开始点的x,y坐标 |
| x1,y1 | 渐变结束点的x,y坐标 |

**addColorStop（stop，color）**规定渐变对象中的颜色和停止位置

​	如果不适用该方法，渐变色将不可见。需要创建至少一个色标。

​	可以多次调用此方法来改变渐变。

| 参数  | 描述                                                 |
| ----- | ---------------------------------------------------- |
| stop  | 介于0.0与0.1之间的值，表示渐变中开始与结束之间的位置 |
| color | 在结束为止显示的CSS颜色值                            |

```javascript
var gradient = ctx.createLinearGradient(0,0,400,0);
gradient.addColorStop("0",'magenta');
gradient.addColorStop('0.5','blue');
gradient.addColorStop('1','red');
ctx.lineWidth = 5;
ctx.strokeStyle = gradient;
ctx.strokeRect(50,50,500,300);

ctx.font='50px Verdana';
ctx.strokeText("hello canvas!",70,120);
```

两个临近stop距离之间的颜色是过渡色。

小于最小stop的部分会按最小stop的color来渲染，大于最大stop的部分会按最大的stop的color来渲染

### 12.1.2、放射渐变

放射性渐变: 从一个点或一个圆向外进行辐射性的颜色渐变

**createRadialGradient（x0,y0,r0,x1,y1,r1）**;创建放射状/环形的渐变对象

| 参数     | 描述                        |
| -------- | --------------------------- |
| x0,y0,r0 | 渐变的开始圆的x,y坐标和半径 |
| x1,y1,r1 | 渐变的结束圆的x,y坐标和半径 |

```javascript
var gradient = ctx.createRadialGradient(100,100,0,100,100,100);
gradient.addColorStop(0,"white");
gradient.addColorStop(1,"green");
// 填充渐变
ctx.fillStyle = gradient;
ctx.fillRect(0,0,200,200);
```

## 12.2、图片填充与合成

**createPattern(image,'repeat \ repeat-x \ repeat-y \ no-repeat')**

​	可在指定的方向内重复指定的元素

​	元素可以是图片、视频或者其他canvas元素

​	被重复的元素可用于绘制/填充矩形、圆形或线条等。

| 参数      | 描述                             |
| --------- | -------------------------------- |
| image     | 规定要使用的图片、画布或视频元素 |
| repeat    | 默认，该模式在水平和垂直方向重复 |
| repeat-x  | 该模式只在水平方向重复           |
| repeat-y  | 该模式只在垂直方向重复           |
| no-repeat | 该模式只显示一次 不重复          |

​	**合成操作**

**globalCompositeOperation属性**  设置如何将一个源图像绘制到目标图像上。

​	源图像-----打算放置到画布上的绘图

​	目标图像--已经放置在画布上的绘图

![1556026180579](D:\大二下\H5程序设计基础\1556026180579.png)

12.3、图片绘制

12.4、像素操作

12.5、动画循环



# 16、渐变与变形处理

## 16.1、渐变效果

### 16.1.1、线性渐变

​	**background:linear-gradient(direction,color-stop1,color-stop2,........);**

**重复的线性渐变：**

​	**background:repeating-linear-gradient(direction,color-stop1,color-stop2,........);**

在一条直线上进行颜色渐变，渐变线由包含渐变图形的容器的中心点和一个角度来定义的。

​	**linear-gradient(to bottom,#fff,#999)；**

第一个参数：制定渐变方向，可以用角度或英文关键词（省略默认180deg）

第二、三个参数：表示颜色的起始点和结束点，可以有多个颜色。

| 角度   | 英文         | 作用           |
| ------ | ------------ | -------------- |
| 0deg   | to top       | 从下到上       |
| 90deg  | to right     | 从左到右       |
| 180deg | to bottom    | 从上到下       |
| 270deg | to left      | 从右到左       |
| 45deg  | to top right | 左下角到右上角 |

```html
//切角效果*/
.div1{
            height: 100px;
            width: 100px;
            background: linear-gradient(45deg,transparent 20px, lightgreen 20px);
        }
```

### 16.1.2、径向渐变

​	**background:radial-gradient(shape at position,color1,color2.....);**

从起点到终点，颜色从内到外进行圆形渐变（从中间向外拉，像圆一样）

shape：

​	circle：圆形；ellipse：椭圆形（默认）

position：

​	关键字：center。。；长度值：px或百分比

```html
.div1{
            background: radial-gradient( 50% 50%,red 0%, yellow 20%,black 50%,green 80%, yellow);
        }
        .div2{
            background: radial-gradient(circle at 50% 50%,red 0%, yellow 20%,black 50%,green 80%, yellow);
        }
        .div3{
            background: radial-gradient(circle at top left,red 0%, yellow 20%,black 50%,green 80%, yellow);
        }
        .div4{
            background: radial-gradient(circle at -10% 50%,red 0%, yellow 20%,black 50%,green 80%, yellow);
        }
```

## 16.2、transform

​	**transform属性用于实现平移、缩放、旋转和倾斜等2D变换。**

### 16.2.1、**transform：translate（）；**

​	translateX(x):元素仅在水平方向移动（X轴移动）

​	translateY(y):元素仅在垂直方向移动（Y轴移动）

### **16.2.2、transform：scale（）；**

​	scaleX(x):元素仅在水平方向缩放

​	scaleY(y):元素仅在垂直方向缩放

​	scale(x,y)：绝对值大于1为放大，绝对值小于1为缩小。值为负数是，是对象的反转。

### **16.2.3、transform：rotate（）；**

​	正角度为顺时针旋转元素；负角度为逆时针旋转元素。

### 16.2.4、transform：skew（）；

​	skewX(x):元素仅在水平方向倾斜

​	skewY(y):元素仅在垂直方向倾斜

参数为负表示向相反方向倾斜。

### 16.2.5、3D变形功能

​	rotateX(angle):围绕X轴以给定的角度旋转

​	rotateY(angle):围绕Y轴以给定的角度旋转

​	rotateZ(angle):围绕Z轴以给定的角度旋转

## 16.3、transform-origin

​	**transform-origin属性更改变换的基点位置**

​	默认情况下，元素基点位置为元素的中心点即x轴和Y轴的中心处

​	CSS3变形进行的位移、缩放、旋转、倾斜都是以元素的基点进行变形。

| 值     | 描述（默认为center，center）                      |
| ------ | ------------------------------------------------- |
| x-axis | 指定远点被置于X轴的可能位置  left\|center\|right% |
| y-axis | 指定远点被置于X轴的可能位置 left\|center\|right%  |

## 16.4、多重变形

​	对同一元素可添加多种变形效果

# 17、CSS3动画

## 17.1、过渡

**transition**通过将元素的某个属性从一个属性值在指定的时间内平滑过渡到另一个属性值来实现动画功能。

## 17.2、动画



# 21、Bootstrap概览及栅格系统

​	Bootstrap基于html、css、JavaScript，响应式。

​	引用Bootstrap之前必须先引用jQuery

Bootstrap包含：基本结构、CSS、组件、JavaScript插件、定制

## 21.1、Bootstrap CSS概览

1.全局设置：

​	Bootstrap使用了html5元素和css属性，必须使用html5文档类型

2.移动设备优先：

​	为确保适当的绘制和触屏缩放，需要在<head>之中添加viewport元素数据标签。

​	•设备上的 viewport 指设备的屏幕上**能用来显示网页的那一块区域**。

​	•添加 viewport 元数据标签可**确保适当的绘制和触屏缩放**。

```html
<meta name="viewport" content="width=device-width,initial-scale=1">
```

| 属性                 | 含义                         |
| -------------------- | ---------------------------- |
| width=device-width   | 表示宽度是设备屏幕的宽度     |
| initial-scale=1.0    | 表示初始的缩放比例           |
| minimum-scale=0.5    | 表示最小的缩放比例           |
| maximum-scale=2.0    | 表示最大的缩放比例           |
| user-scalable=yes/no | 表示用户是否可以调整缩放比例 |

3.排版与链接

Bootstrap排版、链接样式设置了基本的全局样式。分别是：

•为 body 元素设置 background-color: #fff;

•使用 @font-family-base、@font-size-base 和 @line-height-base a变量作为排版的基本参数

•为所有链接设置了基本颜色 @link-color ，并且当链接处于 :hover 状态时才添加下划线

4.布局容器

​	container类、container-fluid类用于包裹页面上的内容。

​	container 类用于固定宽度并支持响应式布局的容器。

​      . container-fluid 类用于 100% 宽度，占据全部视窗的容器。

```html
<style>
	.container{
			background-color:red;/*只显示也中间*/
			height:30px;
	}
	.container-fluid{
			background-color:blue;/*显示在整个宽度内*/
			height:50px;
	}
    @media (min-width: 1200px)
		.container {
    		width: 1170px;
		}
@media (min-width: 992px)
		.container {
   		 	width: 970px;
		}
/*两嵌套个容器类不能相互*/
</style>
```

## 21.2、栅格系统

​	Bootstrap提供了一套响应式、移动设备有限的流式栅格系统，随着屏幕或视窗尺寸的增加，系统会自动分为最多12列。

```html
/*************基本栅格：row col-md-****************/
<div class="container">
    <div class="col">
        <div class="col-md-4"></div>
        <div class="col-md-8"></div>
    </div>
</div>
<--!注意-->
<--!
1、行（row）必须要包含在容器（container）之内。
2、使用行（row）在水平方向创建一组列（col）。
3、内容应当放置于列内，而且，只有列可以作为行的直接子元素。
4、类似.row 和.col-md-4 这些预定义的栅格类可用来快速创建栅格布局。
5、通过设置 padding 创建列之间的间隔。
6、栅格系统中的列是通过指定1到12的值来表示其跨越的范围。例如，三个等宽的列可以使用三个.col-md-4来创建。
7、如果一“行（row）”中包含了的“列（col）”大于 12，多余的列所在的元素将被作为一个整体另起一行排列。
-->
类前缀		col-xs-		col-sm-		col-md-		col-lg-
对应屏幕   超小屏幕		小屏幕 平板	 中等屏幕	   大屏幕 大桌面
/*************偏移列：col-md(xs\sm\lg)-offset-************/
    <将列向右侧偏移。本质是为当前元素增加左侧的边距；>
    <col-md-offset-4:是将col-md-4向右侧偏移4个列的宽度>
/*************列嵌套：在已有的col-md-*中添加新的row**********/
	<在已有的col-md-*中添加新的row并加入col-md-*> 
    <container不能嵌套，嵌套列所包含的列加起来不能超过12列>
/*************列排序：col-md-push-*、col-md-pull-********/ 
    <push是放在后面、pull是放在前面>
<div class="row"> 
    <div class="col-md-9 col-md-push-3">.col-md-9 .col-md-push-3</div> 
    <div class="col-md-3 col-md-pull-9">.col-md-3 .col-md-pull-9</div> 
</div>
```

# 22、Bootstrap 全局CSS(一)

## 22.1、文字排版

1. 内联子标题

   在标题内可以包含<small>标签或.small元素，来标记副标题

   ```html
   <h1> 我真的好<small>漂亮<small></h1>
   ```

2. 页面主题

   Bootstrap将全局font-size设置为14px，line-height为1.428。这些属性直接赋给了<body>和所有段落元素

   p元素被设置了等于1/2行高的地步外边距（10px）

3. 主体副本

   通过添加.lead可以让段落更强调的突出显示。

   ```html 
   <p class="lead">jjjj</p>
   ```

4. 内联文本元素

   1. 标记文本 <mark></mark>
   2. 被删除的文本<del></del>
   3. 无用的文本 <s></s>
   4. 额外插入的文本 <ins></ins>
   5. 带下划线的文本 <u></u>
   6. 小号文本<small></small>

5. 文本对齐

   class="text-left" 	文本左对齐

   class="text-right"	文本右对齐

   class="text-center"     文本中对齐

   class="text-justify"      文本两端对齐

   class="text-nowrap"    禁止文本换行

6. 改变大小写

   class="text-lowercase"	转换成小写

   class="text-uooercase"       转换成大写

   class="text-capitalize"	 首字母大写

7. 缩写

   外观表现为文本底部的虚线框，鼠标移至上面时会变成带有“问号”的指针。当鼠标悬停在上面时会显示完整的文本（需要为 <abbr>的 title属性添加文本）

   ```html
   <abbr title="Woeld Wide Web">WWW</abbr>万维网
   ```

8. 文本强调（文本颜色）

   .text-muted：提示，使用浅灰色（#999）

   .text-primary：主要，使用蓝色（#428bca）

   .text-success：成功，使用浅绿色(#3c763d)

   .text-info：通知信息，使用浅蓝色（#31708f）

   .text-warning：警告，使用黄色（#8a6d3b）

   .text-danger：危险，使用褐色（#a94442）

9. 文本背景颜色

   ```html
   <p class="bg-primary">...</p>
   <p class="bg-success">...</p>
   <p class="bg-info">...</p>
   <p class="bg-warning">...</p>
   <p class="bg-danger">...</p>
   /*链接组件，鼠标经过时，颜色会加深*/
   ```

10. 列表

    Bootstrap 支持有序列表、无序列表和定义列表。

    有序列表：有序列表是指以数字或其他有序字符开头的列表。

    无序列表：无序列表是指没有特定顺序的列表。

    如果不想显示列表项符号，使用 class .list-unstyled来移除样式

11. 内联列表

    通过引用.list-inline将所有列表项放置于同一行

12. 自定义列表

    <dl> 标签定义了自定义列表。

    Ø每个列表项可以包含 <dt> 和 <dd> 元素。

    Ø<dt> 定义列表中的项目。

    Ø<dd> 描述列表中的项目。

    .dl-horizontal 可以让 <dl> 内的**短语及其描述排在一行**。

22.2、代码

22.3、图片