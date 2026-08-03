# 第2章 HTML5新特性

《HTML5移动Web开发（第2版）》

# 学习目标/Target

# 学习目标/Target

# 章节概述/ Summary

随着移动互联网的快速发展，基于HTML5的应用越来越普遍，也变得越来越复杂。为了满足各种各样的需求，HTML5提供了很多新的特性。

HTML5新特性主要包括Web Storage、视频与音频、地理定位、拖曳操作、文件操作和Canvas，这些新特性增强了网页的功能。

本章将针对这些HTML5新特性进行详细讲解。

# 目录/Contents

# 目录/Contents

# Web Storage

2.1

# 2.1 Web Storage

为什么学习Web Storage ：

在HTML5之前，我们通常使用Cookie进行数据存储，例如在本地设备上存储历史活动的信息，但这种方式的缺点是存储的空间大小只有4KB左右，存储的数据解析起来比较复杂。

为此，HTML5提出了网络存储的相关解决方案，即Web Storage（Web存储）。

# 先定一个小目标！

了解Web Storage的概念，能够说出Web Storage的特点

2.1.1  Web Storage的概念

# 2.1.1  Web Storage的概念

Web Storage的作用：

可以将数据存储在本地，如保存用户的偏好设置、复选框的选中状态、文本框默认填写的值等。用户在浏览器中刷新网页时，网页通过Web Storage就可以知道用户之前所做的一些修改，而不需要将用户修改的内容存储在服务器端。

# 2.1.1  Web Storage的概念

Web Storage和Cookie的区别：

类似于Cookie，但相比Cookie可以减少网络流量，因为Web Storage存储的数据不会发送给服务器，而Cookie存储的数据会由浏览器通过HTTP请求自动发送给服务器。

将数据存储在Web Storage可以减少数据在浏览器和服务器间不必要地来回传递。

# 2.1.1  Web Storage的概念

Web Storage中包含两个关键的对象，都是Web Storage的实例，都能使用Web Storage接口提供的方法和属性。

localStorage对象：用于本地存储。

sessionStorage对象：用于区域存储。

# 2.1.1  Web Storage的概念

Web Storage具有以下5个特点：

数据的设置和读取比较方便。

容量较大，可以存储大约5MB数据。

只能存储字符串，如果要存储JSON对象，则可以使用JSON.stringify()和JSON.parse()方法分别进行序列化和反序列化。

本地数据可以即时获得。借助浏览器的缓存，整个页面和数据都可以保存在本地，从本地读数据比通过网络从服务器获得数据快得多，可以立即显示网页中的缓存的内容。

数据可以临时存储。很多时候数据只需要在用户浏览单个页面期间使用，关闭页面后数据就可以丢弃，这种情况使用sessionStorage非常方便。

# 先定一个小目标！

掌握localStorage，能够使用
localStorage提供的属性和方法实现数据的设置、获取和删除

2.1.2  localStorage

# 2.1.2  localStorage

localStorage的主要作用：
本地存储，它可以将数据按照键值对的方式保存在浏览器中，直到用户或者脚本主动清除数据，否则该数据会一直存在。也就是说，使用了本地存储的数据将被持久化保存。

localStorage与sessionStorage的区别：

存储数据的生命周期不同。locaStorage是永久性存储，而sessionStorage的生命周期与会话保持一致，会话结束时数据消失。

从硬件方面理解，localStorage的数据是存储在硬盘中的，关闭浏览器时数据仍然在硬盘上，再次打开浏览器仍然可以获取localStorage保存的数据。而sessionStorage的数据保存在内存中，当浏览器关闭后，内存将被自动清除。

# 2.1.2  localStorage

localStorage的优势：拓展了Cookie的4KB限制，并且可以将第一次请求的数据直接存储到本地，其容量相当于一个5MB大小的数据库。

localStorage也有一些局限：
IE浏览器在8以上版本才支持localStorage。
不同浏览器保存的数据量大小不统一。
目前所有的浏览器都会把localStorage的值类型限定为String类型，对于比较常用的JavaScript对象类型需要转换成字符串保存。
localStorage在浏览器的隐私模式下是不可读取的。
localStorage不能被网络爬虫抓取到。

# 2.1.2  localStorage

localStorage对象提供的方法和属性

| 方法/属性 | 描述 |
|---|---|
| key(n) | 该方法用于返回localStorage对象中第n个key的名称 |
| setItem(key,value) | 该方法接收键名和值作为参数，将会把键值对存储到localStorage中，如果键名存在，则更新其对应的值 |
| getItem(key) | 该方法接收一个键名作为参数，返回键名对应的值 |
| removeItem(key) | 该方法删除键名为key的存储内容 |
| clear() | 该方法清空所有存储内容 |
| length | 该属性返回localStorage对象中包含的item的数量 |

# 2.1.2  localStorage

使用localStorage对象的方法来设置、获取和删除数据：

# 2.1.2  localStorage

使用localStorage对象的方法来设置、获取和删除数据：

# 2.1.2  localStorage

<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Document</title>
</head>
<body>
  <input type="text" id="username">
  <button id="setData">设置数据</button>
  <button id="getData">获取数据</button>
  <button id="delData">删除数据</button>
</body>
</html>

定义按钮
创建C:\code\chapter02\demo01.html，定义用于输入数据的文本框和用于设置数据、获取数据和删除数据的按钮。

# 2.1.2  localStorage

<script>
  var username = document.querySelector('#username');
  // 单击“设置数据”按钮，设置数据
  document.querySelector('#setData').onclick = function () {
    var val = username.value;    // 获取username里面的值
    localStorage.setItem('username', val);
  };
</script>

绑定单击事件
修改demo01.html，在</body>结束标签前添加JavaScript代码，分别获取设置数据、获取数据和删除数据按钮的元素并绑定单击事件。

# 2.1.2  localStorage

// 单击“获取数据”按钮，获得数据
  document.querySelector('#getData').onclick = function () {
    alert(localStorage.getItem('username'));
  };
  // 单击“删除数据”按钮，删除数据
  document.querySelector('#delData').onclick = function () {
    localStorage.removeItem('username');
  };

绑定单击事件
修改demo01.html，在</body>结束标签前添加JavaScript代码，分别获取设置数据、获取数据和删除数据按钮的元素并绑定单击事件。

# 2.1.2  localStorage

在浏览器中访问demo01.html
初始页面效果。

# 2.1.2  localStorage

设置数据
在文本框中输入“admin”，然后单击“设置数据”按钮。

# 2.1.2  localStorage

获取数据
查看数据是否设置成功。如果成功会显示在警告框中。

# 2.1.2  localStorage

删除数据
删除后再次单击“获取数据”的按钮。

# 先定一个小目标！

掌握sessionStorage，能够使用sessionStorage提供的属性和方法实现数据的设置、获取和删除

2.1.3  sessionStorage

# 2.1.3  sessionStorage

sessionStorage的特点：

存储的数据只在当前网页所在的浏览器标签页内有效，只要这个浏览器标签页没有关闭，即使刷新页面或进入同源的另一页面，数据仍然存在。

当浏览器标签页关闭后，sessionStorage中存储的数据将被自动清除。

如果打开了不同的标签页，即使是同一页面，sessionStorage对象也是不同的。所以如果想要让不同标签页下的网页不能互相访问数据，可以将数据保存在sessionStorage中。

sessionStorage对象也提供了一些方法和属性：与localStorage对象的方法和属性类似。

# 2.1.3  sessionStorage

使用sessionStorage对象的方法设置数据，效果如图：

# 2.1.3  sessionStorage

<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Document</title>
</head>
<body>
  <input type="text" id="username">
  <button id="setData">设置数据</button>
</body>
</html>

定义按钮
创建C:\code\chapter02\demo02.html，定义一个文本框和一个“设置数据”按钮，具体代码如下。

# 2.1.3  sessionStorage

<script>
  var username = document.querySelector('#username');
  // 单击“设置数据”按钮，设置数据
  document.querySelector('#setData').onclick = function () {
    var val = username.value;           // 获取username里面的值
    sessionStorage.setItem('username', val);
  };
</script>

绑定单击事件
修改demo02.html，在</body>结束标签前添加JavaScript代码，获取
“设置数据”按钮的元素并绑定单击事件。

# 2.1.3  sessionStorage

在浏览器中访问demo01.html
初始页面效果。

# 2.1.3  sessionStorage

设置数据
在文本框中输入“admin”，然后单击“设置数据”按钮。

# 2.1.3  sessionStorage

打开新标签页，观察数据是否存在
在浏览器重新访问浏览器中访问demo01.html文件，查看sessionStorage中的admin数据是否存在。

# 先定一个小目标！

掌握Web Storage事件监听，能够监听数据的变化

2.1.4  Web Storage事件监听

# 2.1.4  Web Storage事件监听

storage事件触发的条件：

当使用Web Storage存储的数据发生变化时，会触发window对象的storage事件。我们可以监听该事件并指定事件处理函数，当其他页面中的localStorage或sessionStorage中保存的数据发生改变时，就会执行事件处理函数。

# 2.1.4  Web Storage事件监听

监听storage事件的示例代码如下：

// window.addEventListener(事件名, 事件处理函数);
window.addEventListener('storage', function (event) {
console.log(event.key);
});

上述代码中，事件处理函数接收一个event对象作为参数，event对象的key属性保存发生变化的数据的键名。

# 2.1.4  Web Storage事件监听

event对象的属性

| 属性 | 描述 |
|---|---|
| event.key | 获取在sessionStorage或localStorage中被修改的数据键值 |
| event.oldValue | 获取在sessionStorage或localStorage中被修改前的值 |
| event.newValue | 获取在sessionStorage或localStorage中被修改后的值 |
| event.url | 获取在sessionStorage或localStorage中值的页面URL地址 |
| event.storageArea | 获取变动的sessionStorage对象或localStorage对象 |

# 2.1.4  Web Storage事件监听

storage事件并不在导致数据变化的当前页面触发。

如果浏览器同时打开一个域名下面的多个页面，当其中的一个页面改变sessionStorage或localStorage的数据时，其他所有页面的storage事件会被触发，而原始页面并不触发storage事件。通过这种机制，可以实现多个页面之间的通信。

由于sessionStorage无法在不同标签页的网页中互相访问数据，当使用storage事件时，可以将页面放在<iframe>标签创建的框架中，此时在框架内通过storage事件可以监听外层页面的sessionStorage的数据变化。

# 2.1.4  Web Storage事件监听

使用storage事件对页面中的数据进行监听，效果如图：

demo03-1初始页面效果

设置数据

# 2.1.4  Web Storage事件监听

使用storage事件对页面中的数据进行监听，效果如图：

demo03-2初始页面效果

修改后与修改前的用户名

# <!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Document</title>
</head>
<body>
  <label>用户名：</label> <input type="text" id="username">
  <button id="save">保存</button>
  </body>
</html>

定义页面结构
创建C:\code\chapter02\demo03-1.html，定义一个文本框用来输入用户名，定义一个“保存”按钮用来将文本框中的用户名保存在localStorage中。

2.1.4  Web Storage事件监听

# <script>
    var username = document.querySelector('#username');
    // 单击“保存”按钮，设置数据
    document.querySelector('#save').onclick = function () {
      var val = username.value;    // 获取username里面的值
      localStorage.setItem('username', val);
    };
  </script>

获取元素并绑定事件
修改demo03-1.html文件，在</body>结束标签前添加JavaScript代码，获取“保存”按钮的元素并绑定单击事件。

2.1.4  Web Storage事件监听

# 在浏览器中访问demo03-1.html
demo03-1.html初始页面效果如下。

2.1.4  Web Storage事件监听

# 设置数据
在文本框中输入“user1”，单击“保存”按钮。

2.1.4  Web Storage事件监听

# <body>
  <span>新的用户名:</span>
  <span id="newval"></span>
  <br>
  <span>旧的用户名:</span>
  <span id="oldval"></span>
 </body>

监听数据变化并显示
创建C:\code\chapter02\demo03-2.html，通过storage事件监听数据的变化，并定义两个<span>标签用来显示数据修改前和修改后的值。

2.1.4  Web Storage事件监听

# <script>
    var newdata = document.getElementById('newval');
    var olddata = document.getElementById('oldval');
    window.addEventListener('storage', function (e) {
      newdata.innerHTML = e.newValue;     // 设置元素的内容为修改后的值
      olddata.innerHTML = e.oldValue;        // 设置元素的内容为修改前的值
    });
</script>

监听数据变化并显示
修改demo03-2.html文件，在</body>结束标签前添加JavaScript代码，实现数据的监听。

2.1.4  Web Storage事件监听

# 在浏览器中访问demo03-2.html
demo03-2.html初始页面效果。

2.1.4  Web Storage事件监听

# 切换到demo03-1.html页面
在文本框中输入“user2”，单击“保存”按钮。
再切换到demo03-2.html网页。

2.1.4  Web Storage事件监听

# 视频与音频

2.2

# 先定一个小目标！

掌握<video>标签，能够使用<video>标签实现页面中视频效果

2.2.1  <video>标签

# 2.2.1  <video>标签

HTML5为网页提供了处理视频的能力，那么视频在网页中的应用有哪些呢？

# 2.2.1  <video>标签

<video>标签的作用：用于定义视频播放器，它不仅是一个播放视频的标签，还提供了控制栏，用来实现播放、暂停、进度和音量控制、全屏等功能。

<video>标签的基本语法如下：

<video src="视频文件路径" controls>
  浏览器不支持video
</video>

# 2.2.1  <video>标签

<video>标签的基本属性：

src属性：用于设置视频文件的路径。
controls属性：用于为视频提供控制栏。
也可以使用 width和height属性 设置视频宽度和高度。

# 2.2.1  <video>标签

<video>标签支持以下3种视频格式：

Ogg：带有Theora视频编码和Vorbis音频编码的Ogg文件。
MPEG4：带有H.264视频编码和AAC音频编码的MPEG4文件。
WebM：带有VP8视频编码和Vorbis音频编码的WebM文件。

# 2.2.1  <video>标签

<video>标签中可以使用<source>标签指定多个备用的不同格式的文件路径，语法如下：

<video controls>
  <source src="视频文件地址" type="video/格式">
  <source src="视频文件地址" type="video/格式">
</video>

上述代码中，Ogg对应的type为video/ogg，MPEG4对应的type为video/mp4，WebM对应的type为video/webm。

# 2.2.1  <video>标签

创建网页中的视频播放器，效果如图：

# <!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Document</title>
</head>
<body>
  <video controls width="400">
    <source src="video/scenery.mp4" type="video/mp4">
  </video>
</body>
</html>

定义视频播放器
创建C:\code\chapter02\demo04.html，使用<video>标签定义视频播放器。

2.2.1  <video>标签

# 在浏览器中访问demo04.html
页面中显示视频播放器。

2.2.1  <video>标签

# 先定一个小目标！

掌握<audio>标签，能够使用<audio>标签实现页面中音频效果

2.2.2  <audio>标签

# 2.2.2  <audio>标签

HTML5为网页提供了处理音频的能力。音频在网页中种的应用有很多，例如使用网页中QQ音乐播放器听音乐。

# 2.2.2  <audio>标签

<audio>标签的作用：HTML5提供的<audio>标签用来定义Web上的声音文件或音频流。

<audio>标签的基本语法如下：

<audio src="音频文件路径" controls>
  浏览器不支持audio
</audio>

# 2.2.2  <audio>标签

<audio>标签支持以下3种视频格式：

Ogg：Ogg音频格式类似于MP3音频格式。同等条件下，Ogg格式音频文件的音质、体积大小优于MP3音频格式，其音频文件格式表示方式为audio/ogg。

MP3：是一种音频压缩技术，其全称是动态影像专家压缩标准音频层面3（MovingPictureExpertsGroupAudioLayerIII），简称为MP3，它被用来大幅度地降低音频数据量，其音频文件格式表示方式为audio/mp3。

WAV：是录音时用的标准的Windows文件格式，数据本身的格式为PCM或压缩型，属于无损音乐格式的一种，其音频文件格式表示方式为audio/wav。

# 2.2.2  <audio>标签

<audio>标签同样支持引入多个音频源，使用<source>标签使用<source>标签来定义，语法如下：

<audio controls>
  <source src="音频文件地址" type="audio/格式">
  <source src="音频文件地址" type="audio/格式">
</audio>

# 2.2.2  <audio>标签

创建页面中的音频播放器，效果如图：

# 定义音频播放器
创建C:\code\chapter02\demo05.html，使用<audio>标签定义音频播放器。

2.2.2  <audio>标签

<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Document</title>
</head>
<body>
  <audio src="audio/music.mp3" controls>
    您的浏览器不支持audio
  </audio>
</body>
</html>

# 在浏览器中访问demo05.html
页面中显示音频播放器。

2.2.2  <audio>标签

# 先定一个小目标！

掌握video和audio对象，能够使用这些对象的方法和属性实现手动控制视频和音频播放器

2.2.3  video和audio对象

# video和audio对象的常用方法

2.2.3  video和audio对象

| 方法 | 描述 |
|---|---|
| load() | 加载媒体文件，为播放做准备，通常用于播放前的预加载，也用于重新加载媒体文件 |
| play() | 播放媒体文件。如果视频没有加载，则加载并播放；如果视频是暂停的，则变为播放 |
| pause() | 暂停播放媒体文件 |
| canPlayType() | 测试浏览器是否支持指定的媒体类型 |

# video和audio对象的常用属性

2.2.3  video和audio对象

| 属性 | 描述 |
|---|---|
| currentSrc | 返回当前视频/音频的URL |
| currentTime | 设置或返回视频/音频中的当前播放位置（以秒计） |
| duration | 返回视频/音频的长度（以秒计） |
| ended | 返回视频/音频的播放是否已结束 |
| error | 返回表示视频/音频错误状态的MediaError对象 |
| paused | 返回视频/音频是否暂停 |
| muted | 设置或返回是否静音 |
| volume | 设置或返回视频/音频的音量 |

# 2.2.3  video和audio对象

手动控制视频播放器，效果如图：

# <body>
  <video width="300" controls>
    <source src="video/scenery.mp4" type="video/mp4">
  </video>
  <br>
  <button>播放</button>
  <button>暂停</button>
  <button>静音</button>
</body>

定义音频播放器页面结构
创建C:\code\chapter02\demo06.html，使用<video>标签定义视频播放器，并定义3个按钮。

2.2.3  video和audio对象

# <script>
    var video = document.getElementsByTagName('video')[0];
    var btn = document.getElementsByTagName('button');
    btn[0].onclick = function () {
      video.play();
    };
    btn[1].onclick = function () {
      video.pause();
    };
    btn[2].onclick = function () {
      video.muted = !video.muted;
    };
  </script>

设置按钮控制视频播放器
修改demo06.html，添加JavaScript代码，实现手动控制视频的播放、
暂停和静音。

2.2.3  video和audio对象

# 在浏览器中访问demo06.html
页面中显示视频播放器和三个按钮。

设置按钮控制视频的播放、暂停、静音

2.2.3  video和audio对象

# 地理定位

2.3

# 2.3 地理定位

地理定位在日常生活中应用比较广泛，如互联网打车、在线地图等。HTML5增加了获取用户地理位置信息的接口Geolocation，开发者可以通过经纬度来获取用户的地理位置信息。另外，百度等互联网公司也提供了地理定位的接口。

# 先定一个小目标！

熟悉Geolocation地理定位的使用，能够在网页中显示地理定位信息

2.3.1  Geolocation地理定位

# 2.3.1  Geolocation地理定位

Geolocation接口：封装了获取位置信息的技术细节，开发者不需要关心信息的来源，只需关注如何使用即可，这极大地简化了开发的难度。

目前，Geolocation接口已经得到了大部分浏览器的支持：
Firefox
IE 9
Opera
Safari
Chrome

# 2.3.1  Geolocation地理定位

Geolocation的用法：

navigator.geolocation对象提供了getCurrentPosition()方法获取当前地理位置。

navigator是浏览器的内置对象。

当getCurrentPosition()方法被调用时，会发起一个异步请求，浏览器会调用底层的硬件来更新当前的位置信息。

# 2.3.1  Geolocation地理定位

getCurrentPosition()方法的参数说明如下：

getCurrentPosition(successCallback, errorCallback)

successCallback：定位成功时执行的回调函数。

errorCallback：定位失败时执行的回调函数。

# 2.3.1  Geolocation地理定位

当getCurrentPosition()方法成功获取地理信息后，会在successCallback回调函数中传入position对象。该position对象包含coords和timestamp两个属性。

Coords：是一个coordinates对象，包含当前位置的一些信息。

Timestamp：获取到位置的时间戳。

# coords包含的信息

2.3.1  Geolocation地理定位

| 属性名 | 描述 |
|---|---|
| latitude | 十进制表示的纬度坐标 |
| longitude | 十进制表示的经度坐标 |
| accuracy | 当前经纬度信息的精度（单位：m） |
| altitude | 海拔高度（单位：m） |
| altitudeAccuracy | 当前海拔高度的精度 |
| heading | 当前设备的朝向（单位：弧度），从正北开始计算 |

# 2.3.1  Geolocation地理定位

获取用户当前位置信息，效果如图：

页面初始效果

是否允许获取您的位置

获取地理位置

# 2.3.1  Geolocation地理定位

获取用户当前位置信息，效果如图：

设置虚拟地理定位

获取地理位置

# <!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Document</title>
</head>
<body>
  <p id="demo">获得您的坐标：</p>
  <button onclick="getLocation()">试一下</button>
</body>

获取用户当前的经纬度坐标
创建C:\code\chapter02\demo07.html，利用Geolocation进行地理位置定位，获取用户当前的经纬度坐标。

2.3.1  Geolocation地理定位

# <script>
    var x = document.getElementById('demo');
    function getLocation() {
      if (navigator.geolocation) {
        navigator.geolocation.getCurrentPosition(showPosition, showError);
      } else {
        x.innerHTML = '当前浏览器不支持地理定位';
      }
    }
</script>

获取用户当前的经纬度坐标
修改demo07.html，添加JavaScript代码，判断当前浏览器是否支持
地理定位。

2.3.1  Geolocation地理定位

# // 获取定位成功，显示位置信息
    function showPosition(position) {
      x.innerHTML =
        'Latitude:' + position.coords.latitude +         // 纬度
        '<br>Longitude:' + position.coords.longitude;   // 经度
    }

获取用户当前的经纬度坐标
修改demo07.html，继续添加JavaScript代码，定义showPosition()函数，用于显示位置信息。

2.3.1  Geolocation地理定位

# function showError(error) {
      switch (error.code) {
        case error.PERMISSION_DENIED:
          x.innerHTML = '用户拒绝地理定位请求';
          break;
        case error.POSITION_UNAVAILABLE:
          x.innerHTML = '位置信息不可用';
          break;
        case error.TIMEOUT:
          x.innerHTML = '获取用户位置的请求超时';
          break;
        case error.UNKNOWN_ERROR:
          x.innerHTML = '发生了一个不明错误';
          break;
      }
    }

获取用户当前的经纬度坐标
定义showError()函数，用于显示出错信息。

2.3.1  Geolocation地理定位

# 在浏览器中访问demo07.html
初始页面效果。

2.3.1  Geolocation地理定位

# 获取位置
单击“试一下”按钮后，会提示是否允许当前页面获取您的位置。

2.3.1  Geolocation地理定位

# 显示位置信息
单击“允许”按钮后，页面就会显示获取定位后的结果。

2.3.1  Geolocation地理定位

# 设置虚拟地理定位
单击开发者工具右上角的“︙”按钮，在弹出的菜单中选择“More tools”-“Sensors”，然后在Location下拉菜单中选择“Shanghai”，表示虚拟上海的地理位置。

2.3.1  Geolocation地理定位

# 显示位置信息
再次“试一下”按钮，页面显示虚拟位置的信息。

2.3.1  Geolocation地理定位

# 先定一个小目标！

熟悉百度地图地理定位的使用，能够实现百度地图地理定位

2.3.2  百度地图地理定位

# 百度地图的作用：在实际开发中，利用第三方的API（例如百度地图）可以很方便地实现地理定位和信息的获取。百度地图提供了丰富的地图数据库以及地理定位、地图、导航、搜索和路线规划等功能。


百度地图的定位API：基于用户当前位置的，将用户位置（经/纬度）作为参数进行传递，从而实现相应的功能，并支持各类应用的开发者对地理位置的获取需求。

2.3.2  百度地图地理定位

# 2.3.2  百度地图地理定位

实现全景图页面，效果如图：

全景图页面效果

# 进入百度地图开放平台官网
进入百度地图开放平台官网，选择导航栏中的“开发文档”下的“Web开发”，找到“JavaScript API”选项。

2.3.2  百度地图地理定位

# JavaScript API
单击“JavaScript API”，进入以下页面。

2.3.2  百度地图地理定位

# DEMO演示
单击 “JavaScript API v2.0”选项，进入新页面。

2.3.2  百度地图地理定位

# 展示全景图
单击 “DEMO演示”按钮，进入新页面。

2.3.2  百度地图地理定位

# 复制代码并粘贴
创建C:\code\chapter02\demo08.html，复制代码并将代码粘贴到本文件中。

<!DOCTYPE html>
<html>
<head>
  <title>普通地图&全景图</title>
  <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
</head>
<body>
  <div id="panorama"></div>
  <div id="normal_map"></div>
</body>

2.3.2  百度地图地理定位

# 复制代码并粘贴
将代码复制到</head>标签结束前。

<script type="text/javascript" src="http://api.map.baidu.com/api?v=3.0&ak=您的密钥"></script>

2.3.2  百度地图地理定位

# 复制代码并粘贴
将代码复制到</head>标签结束前。

<style type="text/css">
    body,
    html {
      width: 100%;
      height: 100%;
      overflow: hidden;
      margin: 0;
      font-family: "微软雅黑";
    }
    #panorama {
      height: 50%;
      overflow: hidden;
    }
    #normal_map {
      height: 50%;
      overflow: hidden;
    }
</style>

2.3.2  百度地图地理定位

# 复制代码并粘贴
将代码复制到</body>标签结束前。

<script type="text/javascript">
    // 全景图展示
    var panorama = new BMap.Panorama('panorama');
    panorama.setPosition(new BMap.Point(120.320032, 31.589666)); // 根据经纬度坐标展示全景图
    panorama.setPov({ heading: -40, pitch: 6 });
    panorama.addEventListener('position_changed', function (e) {
      // 全景图位置改变后，普通地图中心点也随之改变
      var pos = panorama.getPosition();
      map.setCenter(new BMap.Point(pos.lng, pos.lat));
      marker.setPosition(pos);
    });
</script>

2.3.2  百度地图地理定位

# 复制代码并粘贴
将代码复制到</script>标签结束前。

// 普通地图展示
    var mapOption = {
      mapType: BMAP_NORMAL_MAP,
      maxZoom: 18,
      drawMargin: 0,
      enableFulltimeSpotClick: true,
      enableHighResolution: true
    }
    var map = new BMap.Map("normal_map", mapOption);
    var testpoint = new BMap.Point(120.320032, 31.589666);
    map.centerAndZoom(testpoint, 18);

2.3.2  百度地图地理定位

# 复制代码并粘贴
将代码复制到</script>标签结束前。

var marker = new BMap.Marker(testpoint);
    marker.enableDragging();
    map.addOverlay(marker);
    marker.addEventListener('dragend', function (e) {
      panorama.setPosition(e.point); // 拖动marker后，全景图位置也随着改变
      panorama.setPov({ heading: -40, pitch: 6 });
    });
    map.enableScrollWheelZoom();     // 启用滚轮放大缩小，默认禁用
    map.enableContinuousZoom();      // 启用地图惯性拖拽，默认禁用

2.3.2  百度地图地理定位

# 在浏览器中访问demo08.html
页面显示“百度未授权使用地图API”。

2.3.2  百度地图地理定位

# 申请个人密钥
在百度地图开放平台中申请密钥。

2.3.2  百度地图地理定位

# 复制密钥
申请成功后复制密钥。

2.3.2  百度地图地理定位

# 粘贴密钥
粘贴到demo08.html文件中“您的密钥”位置，保存代码并刷新页面。

2.3.2  百度地图地理定位

# 坐标拾取器
打开百度地图开放平台官网，选择导航栏中的“开发文档”下的“开发者工具”，找到“坐标拾取器”选项。

2.3.2  百度地图地理定位

# 选取坐标
单击“坐标拾取器”后，可以在搜索栏搜索关键字，也可以直接在地图上选择坐标，然后复制右上角的坐标点，粘贴到文件中坐标处。

2.3.2  百度地图地理定位

# 展示坐标对应的全景图
将选取坐标的经纬度复制到代码中，页面显示坐标对应的全景图。

2.3.2  百度地图地理定位

# 拖曳操作

2.4

# 2.4 拖曳操作

拖曳操作的实现：需要借助于鼠标来实现，如文件或图片的移动操作等。

在开发中，我们经常使用原生的JavaScript来实现拖曳效果，实现起来比较复杂。如何让实现拖曳效果变得简单呢？HTML5为我们提供了更好用的接口或者事件，在很大程度上降低了页面中拖曳交互的实现难度。

# 先定一个小目标！

熟悉拖曳的概念，能够说出拖曳的的基本过程

2.4.1  拖曳的概念

# 拖曳的概念：是页面中的元素从初始位置被拖动到新的位置的用户行为，如拖曳页面中的指定元素到另一个元素中。

拖曳过程：首先使用鼠标指针进入源对象，然后按住鼠标左键拖动源对象，当移动鼠标时源对象会跟随鼠标指针移动，如果源对象进入了目标对象，就松开鼠标左键让源对象放置在目标对象中。

2.4.1  拖曳的概念

# 源对象：表示被拖动的元素。为元素添加draggable属性可以设置此元素为源对象，
示例代码如下。

2.4.1  拖曳的概念

<p draggable="true"></p>

<p>标签的draggable属性的值为true，表示<p>标签是一个可以被鼠标拖曳的源对象。

需要注意的是，图片和链接默认是可以拖动的，它们不用添加draggable属性，就可以进行拖曳。

# 目标对象：源对象进入的元素称作目标对象，目标对象可以是页面中的任一元素，
示例代码如下。

2.4.1  拖曳的概念

<div></div>

<div>标签不需要设置draggable属性。

# 先定一个小目标！

掌握拖曳事件，能够实现页面中的拖曳操作

2.4.2  拖曳事件

# 拖曳事件：包括拖曳开始、拖曳进行中、拖曳结束等事件。在开发中，我们可以依靠拖曳事件来实现带有拖曳交互效果的页面。

拖曳事件是由元素对象产生的，如源对象、目标对象，这些对象会产生不同的拖曳事件。

2.4.2  拖曳事件

# 源对象事件

2.4.2  拖曳事件

| 事件 | 事件描述 |
|---|---|
| ondragstart | 当拖曳开始时触发 |
| ondrag | 在拖曳元素被拖曳过程中触发 |
| ondragend | 当拖曳结束时触发 |

# 目标对象事件

2.4.2  拖曳事件

| 事件 | 事件描述 |
|---|---|
| ondragenter | 当源对象进入目标对象时触发 |
| ondragover | 当源对象悬停在目标对象上方时触发 |
| ondragleave | 当源对象离开目标对象时触发 |
| ondrop | 当源对象在目标对象上方释放鼠标时触发 |

# 只有当源对象上的鼠标指针进入目标对象时，才会触发ondragenter事件。
默认情况下，浏览器会默认阻止ondrop事件。

如果想要触发该事件，则需要在ondragover事件中使用“return false;”（或者e.preventDefault()）来阻止其默认行为。

2.4.2  拖曳事件

# 在源对象和目标对象的事件处理函数中，使用dataTransfer对象可以进行数据传输，
示例代码如下：

// 通过dataTransfer对象设置数据
event.dataTransfer.setData(format, data);
// 通过dataTransfer对象获取数据
event.dataTransfer.getData(format);

2.4.2  拖曳事件

# 2.4.2  拖曳事件

event表示事件处理函数的事件源对象


setData(format, data)方法用于将指定格式的数据设置给dataTransfer对象

         参数format用于定义数据的格式

         data表示待设置的数据


getData(format)方法可以从dataTransfer对象中获取指定格式的数据，format表示数据的格式

# 2.4.2  拖曳事件

实现源对象到目标对象的拖曳效果，效果如图：

初始页面效果

# 2.4.2  拖曳事件

实现源对象到目标对象的拖曳效果，效果如图：

源对象拖动事件效果

# 2.4.2  拖曳事件

实现源对象到目标对象的拖曳效果，效果如图：

将源对象拖曳到目标对象中

# <body>
  <div id="div1">
    <p id="p1" draggable="true">拖曳内容1</p>
    <p id="p2" draggable="true">拖曳内容2</p>
    <p id="p3" draggable="true">拖曳内容3</p>
    <p id="p4" draggable="true">拖曳内容4</p>
  </div>
  <div id="div2"></div>
  <div id="div3"></div>
</body>

定义页面结构
创建C:\code\chapter02\demo09.html，定义源对象p和目标对象div页面结构。

2.4.2  拖曳事件

# <style>
    * {
      margin: 0;
      padding: 0;
    }
    div {
      width: 200px;
      height: 200px;
      border: 1px solid red;
      float: left;
      margin: 10px;
    }
</style>

设置元素样式
修改demo09.html，在</head>标签结束前，添加样式代码。

2.4.2  拖曳事件

# div:nth-child(2) {
      border: 1px solid green;
    }
    div:nth-child(3) {
      border: 1px solid blue;
    }
    p {
      height: 25px;
      background-color: pink;
      line-height: 25px;
      text-align: center;
    }

设置元素样式
修改demo09.html，在</head>标签结束前，添加样式代码。

2.4.2  拖曳事件

# 在浏览器中访问demo09.html
页面初始效果如图。

2.4.2  拖曳事件

# 设置源对象的拖动效果
修改demo09.html，在</body>标签结束前添加JavaScript代码。

2.4.2  拖曳事件

<script>
  // 当拖曳开始时触发
  document.ondragstart = function (event) {
    console.log('源对象开始被拖动');
    console.log(event.target.id);
    event.dataTransfer.setData('text/html', event.target.id); // 传递id值
  };
</script>

# 设置源对象的拖动效果
修改demo09.html，在</body>标签结束前添加JavaScript代码。

2.4.2  拖曳事件

// 作用于整个拖曳过程(不断地执行)
  document.ondrag = function (event) {
    console.log('源对象被拖动过程中');
  };
  // 当拖曳结束时触发
  document.ondragend = function (event) {
    console.log('源对象被拖动结束');
  };

# 刷新页面并查看源对象的事件过程
在浏览器中刷新页面，并打开控制台，查看源对象的事件过程。

2.4.2  拖曳事件

# 设置目标对象的释放效果
修改demo09.html，在</script>标签结束前添加JavaScript代码。

2.4.2  拖曳事件

// 当源对象进入目标对象时
document.ondragenter = function (event) {
  console.log('目标对象被源对象拖动着进入');
  console.log(event.target);
};
// 当源对象悬停在目标对象上方时触发
document.ondragover = function(event) {
  console.log('源对象悬停在目标对象上方');
  return false;
};

# 设置目标对象的释放效果
修改demo09.html，在</script>标签结束前添加JavaScript代码。

2.4.2  拖曳事件

// 当源对象离开目标对象时
document.ondragleave = function () {
  console.log('离开了');
};
// 当源对象在目标对象上方释放鼠标时
document.ondrop = function (event){
  console.log('上方释放/松手');
  var id = event.dataTransfer.getData('text/html');
  event.target.appendChild(document.getElementById(id));
};

# 刷新页面进行拖曳操作
在浏览器中刷新页面，然后进行拖曳操作，查看源对象进入目标对象的事件过程。

2.4.2  拖曳事件

# 文件操作

2.5

# 2.5 文件操作

在前端开发中，如果想要把上传成功后的文件内容显示到页面上，或者在上传图片完成后，把图片的缩略图显示到页面中，应该如何实现呢？

这就需要用到HTML5提供的文件读取接口来实现。

# 先定一个小目标！

掌握选择文件，能够在网页中选择文件并读取文件基本信息

2.5.1  选择文件

# 通过上传文件的方式选择文件：

由于Web环境的特殊性，浏览器不允许JavaScript直接访问文件系统。通常我们使用<input type="file" >标签让用户选择文件进行上传。

在默认情况下一个文件域只能上传一个文件。


<input type="file" >标签还有一个multiple属性（HTML5新增），可以实现一次上传多个文件。

2.5.1  选择文件

# 上传多个文件，示例代码：

2.5.1  选择文件

<input type="file" multiple>

在用户选择文件以后，可以得到一个FileList对象，它代表所选的文件列表。

FileList对象是一个类数组的形式，其中包含一个或多个File对象。

如果没有设置multiple属性，或者用户只选择了一个上传文件，那么只需要访问FileList对象的第一个元素。

# 实现在页面中选择文件，效果如图：

2.5.1  选择文件

页面初始效果

查看FileList对象和File对象

# <!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Document</title>
</head>
<body>
  <input type="file" multiple>
</body>
</html>

定义页面结构
创建C:\code\chapter02\demo10.html，定义<input>标签。

2.5.1  选择文件

# <script>
    var input = document.querySelector('input');
    input.onchange = function () {    // 当用户选择文件后执行此事件
      console.log(this.files);         // 查看FileList对象
      var file1 = this.files[0];
      console.log(file1);               //查看File对象
    };
  </script>

上传文件
修改demo10.html，获取input元素，并绑定onchange事件。

2.5.1  选择文件

# 在浏览器中访问demo10.html
页面初始效果如图。

2.5.1  选择文件

# 查看FileList对象和File对象
单击“选择文件”按钮，同时选择1.txt文件和2.txt文件，然后查看开发者工具的控制台。

2.5.1  选择文件

# 先定一个小目标！

掌握FileReader对象，能够使用FileReader对象的常用方法

2.5.2  FileReader对象

# FileReader对象的作用：FileReader对象可以读取本地存储的文件。

在使用FileReader对象前，需要实例化FileReader()构造函数，示例代码如下：

2.5.2  FileReader对象

var reader = new FileReader();

# FileReader对象的常用方法

2.5.2  FileReader对象

| 方法名称 | 参数 | 描述 |
|---|---|---|
| readAsBinaryString() | file | 将文件读取为二进制编码 |
| readAsText() | file,[ending] | 将文件读取为文本 |
| readAsDataURL() | file | 将文件读取为DataURL |
| abort() | (none) | 中断读取操作 |

# 注意：

无论文件是否读取成功，读取文件的方法都不会返回读取的结果，而是将读取结果存储到result属性中。

readAsText()方法完成后，result属性中将包含一个字符串用来表示读取文件的内容。

readAsDataURL()方法完成后，result属性中将包含一个“data:URL”格式的Base64字符串来表示读取文件的内容。

2.5.2  FileReader对象

# 使用FileReader对象读取文件内容的基本语法如下：

2.5.2  FileReader对象

reader.readAsText(File对象);	           // 方式1：读取文本
reader.readAsDataURL(File对象);         // 方式2：读取图片的缩略图

# FileReader对象的常用事件

由于FileReader对象继承EventTarget对象，所以表的事件也可以通过addEventListener()方法来使用。

2.5.2  FileReader对象

| 事件名称 | 描述 |
|---|---|
| onabort | 读取中断时触发 |
| onerror | 读取发生错误时触发 |
| onloadstart | 读取开始时触发 |
| onprogress | 正在读取时触发 |
| onload | 读取成功时触发 |
| onloadend | 读取完成时触发（无论成功或失败） |

# 如何监听文件读取成功事件，示例代码如下：

2.5.2  FileReader对象

// 将读取的内容显示到页面中
reader.onload = function () {	     // onload事件在读取成功时触发
  div.innerHTML = this.result;	    // 将生成的内容显示到页面的div元素中
  img.src = this.result;	         	    // 将生成的内容赋值为img图片的src
};

# 先定一个小目标！

掌握如何读取文件内容，能够进行文件内容的读取

2.5.3  读取文件内容

# 在页面中显示上传成功的图片缩略图，效果如图：

2.5.3  读取文件内容

# <!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Document</title>
</head>
<body>
  <input type="file" multiple><br><br>
  <img src="" alt="缩略图" width="100" height="100">
</body>

定义页面结构
创建C:\code\chapter02\demo11.html，定义页面结构。

2.5.3  读取文件内容

# <script>
    var file = document.querySelector('input');
    var img = document.querySelector('img');
    file.onchange = function () {
      var reader = new FileReader();
      reader.readAsDataURL(this.files[0]);	// 读取文件内容
      reader.onload = function () {
        img.src = this.result;			// 将读取的内容显示到页面中
      };
    };
  </script>

读取文件内容
修改demo11.html，获取表单元素对象并绑定onchange事件。

2.5.3  读取文件内容

# 在浏览器中访问demo11.html
页面中显示图片的缩略图。

2.5.3  读取文件内容

# Canvas

2.6

# 2.6 Canvas

什么是Canvas？

Canvas表示画布，现实生活中的画布是用来作画的。

HTML5中的Canvas ：我们可以称它为“网页中的画布”。默认情况下，Canvas是一块300px*150px的矩形画布，用户可以自定义画布的大小或为画布添加其他属性。

利用Canvas实现绘画：Canvas并不是通过鼠标绘画的，用户需要通过JavaScript来控制画布中的内容，例如添加图片、线条、文字等。

# 先定一个小目标！

掌握<canvas>标签，能够使用<canvas>标签在网页中创建画布

2.6.1  <canvas>标签

# 使用HTML5中的<canvas>标签在网页中创建一个画布，语法格式如下：

<canvas id="cavsElem" width="400" height="300">
  您的浏览器不支持Canvas
</canvas>

上述代码定义了一个id为cavsElem的画布，并设置了画布的宽度为400px，高度为300px。

2.6.1  <canvas>标签

# 通过JavaScript的getElementById()方法获取到网页中的画布对象，代码如下所示：

var canvas = document.getElementById('cavsElem');

上述代码获取了id为cavsElem的画布，同时将获取的画布对象保存在变量canvas中。

2.6.1  <canvas>标签

# context对象：是画布的上下文，也叫做绘制环境，是所有的绘制操作API的入口。

context对象可以使用getContext()方法获得，代码如下所示：

在上述代码中，参数“2d”代表画笔的种类，这里表示二维绘图的画笔。如果想要绘制三维图，可以把参数替换为“webgl”。

2.6.1  <canvas>标签

var context = canvas.getContext('2d');

# 2d：代表一个平面，绘制图形时需要在平面上确定起始点，也就是“从哪里开始画”，这个点需要通过坐标来控制。

Canvas的坐标系：从最左上角“0，0”开始。x轴向右增大，y轴向下增大。

2.6.1  <canvas>标签

# 先定一个小目标！

掌握绘制线条的方法，能够网页中绘制线条

2.6.2  绘制线条

# 线的定义：线是所有复杂图形的组成基础，想要绘制复杂的图形，首先要从绘制线开始。

线的组成：在绘制线之前首先要了解线的组成。一条最简单的线由三部分组成，分别为初始位置、连线端点以及描边。

2.6.2  绘制线条

# 初始位置：在绘制图形时，我们首先需要确定从哪里下“笔”，这个下“笔”的位置就是初始位置。

在画布中使用moveTo(x, y)方法来定义初始位置，其中x和y表示水平坐标轴和垂直坐标轴的位置，中间用“,”隔开。x和y的取值为数字，表示像素值（单位省略）。

2.6.2  绘制线条

设置初始位置的示例代码如下所示：

var context = canvas.getContext('2d');
context.moveTo(x, y);

# 连线端点：在画布中使用lineTo(x, y)方法来定义连线端点。和初始位置类似，连线端点也需要定义x和y的坐标位置。

2.6.2  绘制线条

定义连线端点的代码如下所示：

context.lineTo(x, y);

# 描边：通过初始位置和连线端点可以绘制一条线，但这条线并不能被看到。这时我们需要为线添加描边，让线变得可见。

使用画布中的stroke()方法，可以实现线的可视效果。

2.6.2  绘制线条

设置描边的代码如下所示：

context.stroke();

# 绘制字母M，效果如图：

2.6.2  绘制线条

绘制字母M

# <!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>绘制字母M</title>
</head>
<body>
  <canvas id="cas" width="300" height="300">
    您的浏览器不支持Canvas
  </canvas>
</body>

创建画布
创建C:\code\chapter02\demo12.html，首先创建画布。

2.6.2  绘制线条

# <script>
    var context = document.getElementById('cas').getContext('2d');
    context.moveTo(10, 100);   	// 定义初始位置
    context.lineTo(30, 10);     	// 定义连线端点
    context.lineTo(50, 100);   	// 定义连线端点
    context.lineTo(70, 10);     	// 定义连线端点
    context.lineTo(90, 100);    	// 定义连线端点
    context.stroke();            	// 描边
  </script>

绘制字母M
修改demo12.html，添加JavaScript代码，绘制字母M。

2.6.2  绘制线条

# 在浏览器中访问demo12.html
页面中显示字母M。

2.6.2  绘制线条

# 先定一个小目标！

掌握设置线条的样式的方法，能够实现设置不同样式的线条

2.6.3  设置线条的样式

# 设置线条宽度：使用lineWidth属性可以定义线的宽度，该属性的取值为数值（不带单位），以像素为计量。

设置线的宽度的示例代码如下所示：

context.lineWidth = '10';

2.6.3  设置线条的样式

上述代码中设置了线的宽度为10。

# 设置描边颜色：使用strokeStyle属性可以定义线的描边颜色，该属性的取值为十六进制颜色值或颜色的英文名。

设置描边颜色的示例代码如下所示：

context.strokeStyle = '#f00';
context.strokeStyle = 'red';

2.6.3  设置线条的样式

上述代码中两种方式都可以用于设置线的描边颜色为红色。

# 设置端点形状：默认情况下，线的端点是方形的，通过lineCap属性可以改变端点的形状。

设置端点形状的示例代码如下所示：

context.lineCap = '属性值';

2.6.3  设置线条的样式

lineCap属性的取值有3个：

butt（默认值）：默认效果，无端点，显示直线方形边缘

round：显示圆形端点

square：显示方形端点

# 绘制带有样式的线条，效果如图：

2.6.3  设置线条的样式

# <!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>绘制字母M</title>
</head>
<body>
  <canvas id="cas" width="300" height="300">
    您的浏览器不支持Canvas
  </canvas>
</body>

创建画布
创建C:\code\chapter02\demo13.html，创建画布。

2.6.3  设置线条的样式

# <script>
    var context = document.getElementById('cas').getContext('2d');
    context.moveTo(10, 10);      	// 定义初始位置
    context.lineTo(300, 10);      	// 定义连线端点
    context.lineWidth = '10';     	// 设置线的宽度
    context.strokeStyle = 'red';  	// 设置线的颜色
    context.lineCap = 'round';    	// 设置线的端点形状
    context.stroke();               	// 定义描边
  </script>

设置线的宽度、颜色和端点形状
修改demo13.html，添加JavaScript代码，设置线的宽度、颜色和端点形状。

2.6.3  设置线条的样式

# 在浏览器中访问demo13.html
页面显示一条红色的线。

2.6.3  设置线条的样式

# 先定一个小目标！

掌握设置线条的路径的方法，能够在网页中绘制图形

2.6.4  设置线条的路径

# 路径的定义：路径是所有图形绘制的基础，通过初始位置和连线端点即可创建一条路径。

路径需要通过路径状态进行重置或闭合，来产生不同的路径样式。

路径的状态：

重置路径

闭合路径

2.6.4  设置线条的路径

# 重置路径的概念：

在同一画布中，即使我们添加再多的连线端点也只能有一条路径，如果想要开始新的路径就需要使用beginPath()方法，当出现beginPath()时即表示路径重新开始。

2.6.4  设置线条的路径

# 绘制两条不同样式的线条，效果如图：

2.6.4  设置线条的路径

重置路径

未重置路径

# <!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>绘制字母M</title>
</head>
<body>
  <canvas id="cas" width="300" height="300">
    您的浏览器不支持Canvas
  </canvas>
</body>

创建画布
创建C:\code\chapter02\demo14.html，创建画布并绘制不同样式的线条。

2.6.4  设置线条的路径

# <script>
    var context = document.getElementById('cas').getContext('2d');
    context.moveTo(10, 10);       		// 定义初始位置
    context.lineTo(300, 10);      		// 定义连线端点
    context.lineWidth = '5';       		// 设置线的宽度
    context.strokeStyle = '#00f';   		// 设置线的颜色
    context.stroke();               		// 描边
    context.beginPath();               	                    // 重置路径
    context.moveTo(10, 50);         	                    // 定义初始位置
    context.lineTo(300, 50);        	                    // 定义连线端点
    context.lineWidth = '10';        	                    // 设置线的宽度
    context.strokeStyle = '#f00';   	                    // 设置线的颜色
    context.stroke();               		// 描边
  </script>

重置路径
修改demo14.html，添加JavaScript代码，重置路径。

2.6.4  设置线条的路径

# 在浏览器中访问demo14.html
页面中显示一条蓝色的线和一条红色的线。

2.6.4  设置线条的路径

# 去掉context.beginPath()
刷新页面，页面中显示两条样式相同的线。

2.6.4  设置线条的路径

未重置路径

# 闭合路径的概念：

闭合路径就是将我们绘制的开放路径进行封闭处理，多点的路径闭合后会形成特定的形状。在画布中使用closePsth()方法闭合路径。

2.6.4  设置线条的路径

# 绘制三角形并填充，效果如图：

2.6.4  设置线条的路径

设置闭合路径

填充图形

# <!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>绘制字母M</title>
</head>
<body>
  <canvas id="cas" width="300" height="300">
    您的浏览器不支持Canvas
  </canvas>
</body>

创建画布
创建C:\code\chapter02\demo15.html，创建画布。

2.6.4  设置线条的路径

# <script>
    var context = document.getElementById('cas').getContext('2d');
    context.moveTo(10, 10);      	// 定义初始位置
    context.lineTo(10, 100);     	// 定义连线端点
    context.lineTo(100, 100);     	// 定义连线端点
    context.stroke();             	// 描边
  </script>

绘制L线
修改demo15.html，添加JavaScript代码，绘制L线。

2.6.4  设置线条的路径

# 在浏览器中访问demo15.html
页面中显示L线。

2.6.4  设置线条的路径

# 设置闭合路径
修改demo15.html，使用closePath()方法设置闭合路径。

2.6.4  设置线条的路径

<script>
    var context = document.getElementById('cas').getContext('2d');
    context.moveTo(10, 10);      	// 定义初始位置
    context.lineTo(10, 100);     	// 定义连线端点
    context.lineTo(100, 100);     	// 定义连线端点
    context.closePath();
    context.stroke();             	// 描边
  </script>

# 刷新页面
页面中显示一个三角形。

2.6.4  设置线条的路径

# 填充图形
修改demo15.html，使用fill()方法填充图形。

2.6.4  设置线条的路径

<script>
    var context = document.getElementById('cas').getContext('2d');
    context.moveTo(10, 10);      	// 定义初始位置
    context.lineTo(10, 100);     	// 定义连线端点
    context.lineTo(100, 100);     	// 定义连线端点
    context.closePath();                         // 设置闭合路径
    context.fill();                                    // 填充图形
    context.stroke();                              // 描边
  </script>

# 刷新页面
页面中显示一个填充颜色为黑色的三角形。

2.6.4  设置线条的路径

# 使用fillStyle属性可以更改填充颜色：

fillStyle属性的取值为十六进制颜色值或英文颜色名。例如，填充红色，在fill()方法调用前添加如下代码即可：

2.6.4  设置线条的路径

context.fillStyle = '#f00';		// 方式1
context.fillStyle = 'red';		// 方式2

# 本章小结

本章主要讲解了HTML5新特性的使用，包括Web Storage、视频与音频、地理定位、拖曳操作、文件操作以及Canvas。学习本章内容后，读者应该能够利用这些HTML5新特性增强网页的功能，为HTML5移动Web开发奠定基础。

本

章

小

结