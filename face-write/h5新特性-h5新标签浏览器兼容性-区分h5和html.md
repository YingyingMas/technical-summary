新特性：
1. 拖拽释放(Drag and drop) API
2. 语义化更好的内容标签（header,nav,footer,aside,article,section）
3. 音频、视频API(audio,video)
4. 画布(Canvas) API
5. 地理(Geolocation) API  
6. 本地离线存储 localStorage 长期存储数据，浏览器关闭后数据不丢失；
7. sessionStorage 的数据在浏览器关闭后自动删除
8. 表单控件，calendar、date、time、email、url、search  
9. 新的技术webworker, websocket, Geolocation

移除的元素：
1. 纯表现的元素：basefont，big，center，font, s，strike，tt，u；
2. 对可用性产生负面影响的元素：frame，frameset，noframes；

支持HTML5新标签：
1. IE8/IE7/IE6支持通过 document.createElement 方法产生的标签，可以利用这一特性让这些浏览器支持 HTML5 新标签，浏览器支持新标签后，还需要添加标签默认的样式（当然最好的方式是直接使用成熟的框架、使用最多的是html5shim框架）：
```
  <!--[if lt IE 9]>
  
  <script> src="http://html5shim.googlecode.com/svn/trunk/html5.js"</script>
  
  <![endif]-->
```

如何区分：
1. DOCTYPE声明
2. 新增的结构元素
3. 功能元素

# ------------------------------------------
（Continue writing by mayingying）

### 1.拖放

[demo](https://github.com/YingyingMas/technical-summary/blob/master/html/1.h5-drag.html)

### 2.Geolocation [dʒɪɒləʊ'keɪʃn] 

> Geolocation 接口是一个用来获取设备地理位置的可编程的对象，
  它可以让Web内容访问到设备的地理位置，
  这将允许Web应用基于用户的地理位置提供定制的信息。
  其实 Geolocation 就是用来获取到当前设备的经纬度（位置）
  
> 带有此接口的对象：Navigator，
  Navigator.geolocation 只读属性返回一个 Geolocation 对象 
  
[demo](https://github.com/YingyingMas/technical-summary/blob/master/html/2.h5-geolocation.html)

### 3.websocket

