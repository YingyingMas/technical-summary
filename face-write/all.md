# 汇总

## HTML

### h5新特性

1. 拖拽功能，draggable属性，其中有ondragstart，ondrop，ondragover方法；
2. 新增Web Storage机制进行数据存储：localStorage 和 sessionStorage；
3. Geolocation可编程对象用于获取到当前设备的经纬度；比如说h5页面调用地图，获取用户位置。
4. input元素的新类型：date, email, url等；
5. 新增语义化标签，如header,nav,footer,aside,article,section等，还有非常重要的新媒体解决方案：音频、视频audio,video标签，绘制图像的canvas js绘制图形，webGL 3d绘制;
6. 新的全域属性如：
    - contentEditable属性：允许用户在线编辑元素中的内容，暂时还没有特别的API来保存修改后的内容；
    - tabindex属性：当不断按Tab键时，让其获得焦点，tabindex属性表示该控件是第几个被访问到的；
    - hidden属性：与display: none相似，元素消失，不占用页面空间。
7. h5唯一的文件类型声明：<!DOCTYPE HTML>，h4:<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//....很多标准">；
8. WebSocket：网络通信协议，服务器可以主动向客户端推送信息，客户端也可以主动向服务器发送信息，属于服务器推送技术的一种；
9. Web Worker：
    - 运行在主线程之外的执行线程，用来执行耗时的js脚本；
    - 不会影响主线程上的活动，独立于其他脚本；
    - 不能用来操作DOM和BOM；
    - new worker(''a.js');主线程onmessage监听，a.js执行完postMessage给主线程发送消息；
10. requestAnimationFrame 动画
HTML语义化：使用恰当语义的html标签，让页面具有良好的结构与含义。对开发者友好，增强了可读性。对机器友好，有益于爬虫爬取有效信息

### XHTML和HTML

XML：

- 定义：可扩展标记语言；
- 设计目的：传输和存储 数据；
- 焦点：数据的内容；
- 特点：没有预定义标签，需自定义，具有自我描述性的纯文本。

HTML：

- 定义：超文本标记语言；
- 设计目的：显示数据；
- 焦点：数据的外观；
- 特点：预定义标签

XHTML：

- 定义：可扩展超文本标签语言，用XML规则规范的HTML；
- 设计目的：规范编写良好结构的文档；
- 特点：更严谨更纯净的 HTML，如：标签必须正确地嵌套、必须关闭、必须用小写字母、必须拥有根元素。

### @media媒体查询

允许内容的呈现针对一个特定范围的输出设备而进行裁剪，适合web网页应对不同型号的设备而做出对应的响应适配。

媒体类型:

- all（所有）
- handheld（手持）
- print（印刷）
- projection（投影）
- screen（屏幕）

 属性：

- width：浏览器宽度
- height：浏览器高度
- device-width：设备屏幕分辨率的宽度值
- device-height：设备屏幕分辨率的高度值
- orientation：浏览器窗口的方向纵向还是横向
- aspect-ratio：比例值，浏览器的纵横比。
- device-aspect-ratio：比例值，屏幕的纵横比。

书写：@media + 媒体类型 + and +

- 打印样式：@media print {}
- 手机等小屏幕手持设备： @media screen and (min-width: 320px) and (max-width: 480px) {}
- 平板之类的宽度 1024 以下设备：@media only screen and (min-width: 321px) and (max-width: 1024px) {}
- PC客户端或大屏幕设备: 1028px 至更大：@media only screen and (min-width: 1029px) {}
- 竖屏：@media screen and (orientation:portrait) {}
- 横屏：@media screen and (orientation:landscape){}

### link与@import

- link：HTML标签，加载CSS文件，定义rel连接属性等。与页面同步加载。
- @import：CSS语法规则，导入样式表。页面加载完毕后被加载

### CSS选择器的优先级

- !important > 内联样式 > ID选择器 > 类选择器 > 标签选择器 > 通配符 > 继承 > 浏览器默认属性
- 选择器比较：{是否有内联样式(0/1), ID选择器次数, 类选择器+属性选择器+伪类总次数，标签选择器+伪元素总次数}，
- 从左到右，一一比较，直到比出大值，即可停止。

### 定位

- 1、static 默认值静态定位。
- 2、relative相对于原位置定位，不脱离文档流。
- 3、absolute相对于最近的非static定位的父元素定位脱，离文档流，;如果没有非static定位的父元素，则相对于“浏览器可视窗口”定位。
- 4、fixed是相对于“浏览器的可视窗口”来定位，脱离文档流。

### css单位px,rem,em的区别

 > px：相对长度单位，相对于显示器屏幕分辨率而言。
 > em：相对长度单位。相对于父元素的font-size，如当前父元素的字体尺寸未设置，则相对于浏览器的默认字体尺寸
 > rem：相对长度单位，相对于HTML根元素的字体大小来计算。解决移动端多屏适配布局问题，针对不同手机屏幕尺寸通过媒体查询动态的改变根节点html的font-size大小(基准值)。
   rem计算：设计稿任意元素尺寸px*（设备屏幕px/设计稿尺寸px）/(html的font-size)

### 严格模式与混杂模式

doctype文档类型声明，告诉浏览器解析器用什么标准解析当前文档。

文档类型检测document.compatMode：

- CSS1Compat：标准模式（严格模式），浏览器按照W3C标准解析渲染页面；
- BackCompat：混杂模式（怪异模式），文档类型默认值，浏览器按照自己的方式解析渲染页面，在不同的浏览器就会显示不同的样式。

> DOCTYPE不存在或形式不正确会导致HTML和XHTML文档以混杂模式呈现。
> HTML5没有严格和混杂之分，只有一种声明方式<!DOCTYPE html>，浏览器以严格模式规则解析。

### 重绘Repaint和重排/回流reflow

- 重绘：当元素的一部分属性发生改变，如外观、背景、颜色等不会引起布局变化，只需要浏览器根据元素的新属性重新绘制，使元素呈现新的外观叫做重绘。
- 回流：当一部分或者全部元素因为大小边距等问题发生改变而需要DOM树重新计算的过程。必定引起重绘。
- 影响：破坏用户体验，让UI展示非常迟缓，重排性能影响更大。

如何产生：

1. 增删改DOM节点；
2. display：none触发重绘和重排；，visibility：hidden触发重绘；
3. DOM动画；
4. 改变style；
5. 用户改变窗口字号。

如何避免：

1. 当DOM的几个样式同时改变时定义一个新的className，不要一个一个的修改；
2. 先display:none隐藏元素，然后对元素进行所有操作，最后再显示该元素；
3. 动画效果使用position属性absolute或者fixed让元素脱离动画流，减少回流的render tree的规模；
4. 避免使用CSS的JavaScript表达式。
5. 减少dom的操作；
6. 创建游离于dom树之外的节点，在此上操作完再插进文档只触发一次重排。
7. 提升为合成层，单独的图层，交由GPU处理。transform使浏览器为元素创建一个 GPU 图层，repaint不打扰别人。(opacity/translate/rotate/scale获得GPU加速)

### visibility: hidden和display: none的区别

1. 父元素设置visibility:hidden;子元素会继承这个属性。但如果重新给子元素设置visibility: visible，则子元素又会显示出来。display: none不会；
2. visibility: hidden(仅仅是重绘)。display: none（重绘加重排）；
3. CSS3的transition支持visibility属性，但是并不支持display，由于transition可以延迟执行，因此可以配合visibility使用纯css实现hover延时显示效果。提高用户体验。

### 盒模型

文档布局时，将所有元素表示为一个个矩形的盒子，CSS决定这些盒子的属性。
盒模型由content、padding、border、margin组成。

标准盒模型：width = content
怪异盒模型：width = border(左右) + padding(左右) + content

虽然现代浏览器默认使用标准盒模型，但是在不少情况下怪异盒模型更好用，于是在css3中加入box-sizing。

- box-sizing: content-box // 标准盒模型
- box-sizing: border-box  // 怪异盒模型

我们常用的是标准盒模型，box-sizing: content-box，width指的是内容的宽高，并不是盒子的宽高，
盒子的宽高是内容+padding+border，但这种方式在我们真是项目中就会有一个问题，比如我想一个盒子的大小是100*100，但是我改了边框大小，那盒子的内容还得调式，
所以在真实项目中常用的是box-sizing: border-box，设置成怪异盒模型，盒子的高度是内容+padding+border，修改padding、border会自动调内容宽高。
包括一些UI库的源码里面也是采用的border-box的模型。
还有一种弹性伸缩盒模型，虽然是一种布局方式，但也有人称其为一种盒模型，在这个盒子里有两个轴，主轴和交叉轴，盒子里所有的子元素就是flex item，
默认所有项是靠着交叉轴的上方和主轴的左方排列的，但是我们可以通过justify-content和align-items控制所有项在主轴和交叉轴的排列方式和伸缩设置。

多列布局
这种布局一般在文章类的页面会有这种布局，一页面分很多列，每一列之间相隔多少间距。但实际需求上很少使用。

### 层叠上下文

HTML元素的三维概念，相对于网页的z轴延伸。
如何产生：

1. HTML根元素本身具备。
2. z-index 值不为"auto"的绝对/相对定位元素。
3. z-index 值不为"auto"的flex项目。
4. opacity 值不为 1。
5. transform 值不为 none。
6. filter 值不为 none。

层叠准则：
index为负 -> block -> float -> inline -> index为0 -> index为正，值相同则后来居上。

### 块级格式化上下文BFC

一个独立的渲染区域，规定了里面块级元素的布局，BFC内部与外部元素互相隔离。
如何触发：

1. HTML根元素本身具备。
2. position 值为 fixed、absolute
3. float 值不为 none。
4. overflow 值不为 visible。
5. display 值为 inline-block、table-cell、table-caption

作用：

1. 防止margin发生重叠。
2. 防止元素被浮动元素覆盖，同级俩盒子，元素1浮动，元素2块元素+BFC 。
3. BFC元素可以被内部浮动盒子撑开。

### 弹性盒子

Flex布局子元素的float、clear和vertical-align属性将失效.
只声明布局应该有行为，浏览器负责完成实际布局，当布局涉及到不定宽度，分布对齐的场景时，优先考虑弹性盒布局。

Flex容器属性：

1. flex-direction：flex项目的主轴/排列方向
   - row（默）：主轴在水平方向，起点在左。
   - row-reverse：主轴在水平方向，起点在右。
   - column：主轴在垂直方向，起点在上。
   - column-reverse：主轴在垂直方向，起点在下。

2. flex-wrap：定义在一条轴线排不下时如何换行
   - nowrap（默）：不换行。
   - wrap：换行，第一行在上。
   - wrap-reverse：换行，第一行在下。

3. flex-flow：1和2的简写形式
   - flex-flow: row  nowrap;

4. justify-content：定义了项目在主轴上的对齐方式
   - flex-start（默）：左对齐
   - flex-end：右对齐
   - center： 居中
   - space-between：两端对齐，项目之间的间隔相等。
   - space-around：每个项目两侧的间隔相等。so项目之间的间隔比项目与边框的间隔大一倍。

5. align-items：定义项目在交叉轴上如何对齐
   - flex-start：交叉轴的起点对齐。
   - flex-end：交叉轴的终点对齐。
   - center：交叉轴的中点对齐。
   - baseline: 项目的第一行文字的基线对齐。
   - stretch（默认值）：如果项目未设置高度或设为auto，将占满整个容器的高度。

6. align-content：定义了当有多根轴线的时候对齐方式
   - flex-start：交叉轴的起点对齐。
   - flex-end：交叉轴的终点对齐。
   - center：交叉轴的中点对齐。
   - space-between：交叉轴两端对齐，轴线之间的间隔平均分布。
   - space-around：每根轴线两侧的间隔都相等。so轴线之间的间隔比轴线与边框的间隔大一倍。
   - stretch（默认值）：轴线占满整个交叉轴。

Flex项目属性：

1. order：定义项目排序，值为num，按值排序。

2. flex-grow：定义项目的放大比例
   - 默认0：在剩余空间也不放大
   - 所有item均为1：等分剩余空间
   - 值不等：按比例分配剩余空间。

3. flex-shrink：定义了项目的缩小比例
   - 默认1：空间不足将缩小该项目
   - 所有item均为1：等比例缩小
   - 值不等：按比例缩小。

4. flex-basis：定义了在分配多余空间之前项目占据的主轴空间
   - 默认auto：项目本来大小
   - 设为固定值：占据固定空间.

5. flex：1、2、3的简写
   - flex: 1 1 auto; === flex:auto;
   - flex: 0 0 auto; === flex:none;
   - flex为一个非负数字n：该数字为flex-grow的值；flex-shrink：1；flex-basis：0%；
   - flex为两个非负数字n1，n2：分别为flex-grow和flex-shrink的值，flex-basis：0%；
   - flex为一个长度或百分比：视为flex-basis的值，flex-grow：1；flex-shrink：1；

6. align-self：允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性
   - 默认auto，继承align-items属性
   - align-self: auto | flex-start | flex-end | center | baseline | stretch;
（参考：<http://www.ruanyifeng.com/blog/2015/07/flex-examples.html>）

### meta

 meta 元素提供有关页面的元信息，标签的属性定义了与文档相关联的名称/值对

- name 属性 + content 属性：元信息的名称和值

    ```html
        <!--双核浏览器指定文档渲染模式-->
        <meta name="renderer" content="webkit">
        <!--Keywords 网页关键字-->
        <meta name="keywords" content="嘻嘻">
        <!--description 网站内容描述-->
        <meta name="description" content="我是嘻嘻">
        <!--author 作者-->
        <meta name="author" content="小马">
    ```

- charset 属性：描述档编码形式

    ```html
        <meta charset="utf-8">
    ```

- http-equiv 属性 + content 属性：相当于http文件头作用，向浏览器传回信息

    ```html
        <!--expires 设定网页到期时间。一旦网页过期，必须到服务器上重新传输-->
        <meta http-equiv="expires" content="Tue, 01 Jan 1980 1:00:00 GMT">
        <!--pragmacache模式，禁止浏览器从本地计算机的缓存中访问页面内容。-->
        <meta http-equiv="pragma" content="no-cache">
        <!--refresh 如：指停留2秒钟后自动刷新到URL网址-->
        <meta http-equiv="refresh" content="2;URL=http://www.myy.net">
         <!--content-type 设定页面使用的字符集-->
        <meta http-equiv="content-type" content="text/html;charset=gb2312">
        <!--cache-control 指定请求和响应遵循的缓存机制-->
        <meta http-equiv="cache-control" content="no-cache, no-store" />
    ```

- viewport 属性，窗口

    ```html
        <meta name="viewport" content="width=device-width,
                                   initial-scale=1,
                                   minimum-scale=1,
                                   maximum-scale=1,
                                   user-scalable=no">
    ```

## JavaScript

### null与undefined的区别

null最初是一个表示"无"的对象，转为数值时为0，表示"没有对象"，即该处不应该有值。一个值赋值等于null它才是nul。
null一般都是开始不知道值，我们手动先设置为null，后期再给予赋值操作，是意料之中的。

undefined一个表示"无"的原始值，转为数值时为NaN，表示"缺少值"，就是此处应该有一个值，但是还没有定义。

### 精度丢失

JS 的 Number 类型遵循的是 IEEE 754 标准，以 0.1 转换为 IEEE 754 标准转换的过程：
会将 0.1 转换为二进制表示，会出现无限重复
将转换后的二进制通过科学计数法表示，
将通过科学计数法表示的二进制转换为 IEEE 754 标准表示。
转换为十进制计算精度就出现了问题。

### 基本类型（值） 和  复杂类型（引用）

基本类型

- 变量存的是值
- 存放在栈内存的
- 值是不可变得
- 在赋值的时候拷贝值

复杂类型

- 变量存的是内存地址
- 存储需要内存的栈内存和堆内存共同完成，栈区内存保存变量标识符和指向堆内存中该对象的指针,指向堆中的对象.
- 值是可变的
- 在赋值的时候只拷贝地址，不拷贝值。

内存分配中的栈和堆：

- 从硬件上说，堆和栈最终都是内存条上的若干存储单元，没有什么不同。
- 但是程序存运行时需要拷到内存中执行，内存会分别存储不同的信息，
- 栈内存分配局部变量空间，一般存放函数的参数值、局部变量的值等，由编译器自动分配和释放。
- 堆内存用于分配程序员申请的内存空间

### cookies、sessionStorage和localStorage/前端本地存储

1. 作用域：Web Storage和cookie均受同域限制，某网页存入数据，只有同域下的网页才能读取。sessionStorage不会跨标签页存储，而localStorage会跨标签页存储。
2. 存取位置：cookie数据始终会在同源的http请求中携带，在浏览器和服务器间来回传递；sessionStorage和localStorage只存在于浏览器会话中；
3. 存储大小：cookie数据不能超过4K，sessionStorage和localStorage的存储空间是浏览器决定的，可达5M；
4. 有效期：Cookie生成时会被指定一个Expire值为其生存周期，超出周期Cookie就会被清除，sessionStorage 当前页面关闭即失效；localStorage：没有过期时间，直到手动去删除。
5. web Storage支持事件通知机制，可以将数据更新的通知发送给监听者  ```window.addEventListener('storage', function(e) {})```

WebSQL：已废弃，关系型数据库，支持复杂的查询，被IndexedDB取代
IndexedDB：HTML5标准数据库储存方案，使用浏览器存储大量数据，可以离线使用，以key-value型存储。

### this的理解

this的指向是在运行时基于函数的执行环境确定的。
1. 默认绑定：this是指向全局对象的，浏览器中指向window；
2. 隐式绑定：函数被调用的位置存在上下文对象时，指向这个对象；
3. 显式绑定：显示改变this指向，call、apply、bind；
4. new绑定：构造函数创建新对象，新对象绑定到构造函数的this，构造函数内this指向新对象。
5. vue中的this：Vue所有的生命周期钩子方法以及挂载在vue实例上的函数this指向调用它的Vue实例。
6. 箭头函数没有属于自己的this，所谓的this是其执行上下文继承而来的this。

### 预解释、执行环境、作用域链、闭包

预解释：
  > 代码执行器引擎对代码进行预处理，先解析代码，变量提升，获取所有被声明的变量，提升到代码的头部，然后再一行一行地运行。
  > 读取当前作用域变量，创建变量，如有相同声明，则忽略此声明继续进行解析。
  > 而后进行赋值操作，在当前作用域中寻找变量,未找到则向上级作用域询问。

执行环境：
  > 预解释的同时创建了执行环境，js中每个函数都有自己的执行环境，定义了变量和函数有权访问的其他数据，执行完毕后被销毁。

作用域链：
  > 执行环境中含有外部环境的引用，用获取外部环境的变量、声明等，这些引用串联起来一直指向全局环境，就形成了作用域链。

闭包：
  > 闭包是能够访问外部函数变量的一个函数，
  > 而函数是保存在内存中的对象，所以位于函数执行上下文中的所有变量也需要保存在内存中，这样就不会被回收，
  > 如果一旦循环引用或创建闭包，就会占据大量内存，可能会引起内存泄漏。

js运行机制：
  > JavaScript引擎：编译并执行js代码，完成内存分配、垃圾回收等，组成：内存堆( 内存分配地址的地方) + 调用栈(代码执行的地方)
  > JavaScript运行时：提供对象，事件交互等。
  > 执行函数，进入调用栈，创建执行上下文，创建变量对象，开始执行。根据执行条件决定this指向。
  > 可执行上下文中的词法环境中含有外部词法环境的引用，通过这个引用获取外部环境的变量就产生了闭包，这些引用串联起来一直指向全局词法环境就形成了作用域链。

### 原型

 原型对象：prototype
 每个函数创建时候都有一个prototype属性，指向原型对象，包含特定类型所有实例共享的属性和方法。Person.prototype
 原型对象有一个属性constructor，指向原型对象所在的函数。Person.prototype.constructor -> Person

 原型链：
 由构造函数创建的实例都有一个__proto__属性，指向函数的原型对象，上游的原型对象也有一个__proto__，这样就形成了原型链。
 person.__proto__ -> Person.prototype，用来描述对象的继承结构。

 继承：
 继承指的是实例对象可以使用其__proto__属性所指向的原型对象上面的属性和方法。一个对象继承的所有对象串起来就是这个对象的原型链。

 继承的方式：
 1. 给原型对象动态添加属性和方法：A.prototype.demo = ...
 2. 覆写构造函数的prototype属性：A.prototype = ...
 3. 多继承：for循环将一个对象A的所有属性copy一份到构造函数B的原型对象上去，那么构造函数B的所有实例就可以使用这些个A对象的属性和方法了
 4. var A = Object.create(B)，A继承了B的属性和方法
 5. 借用Object.create()覆写原型对象，A.prototype = Object.create(B)
 6. A.prototype = new B()，A的实例继承了B.prototype

### GET和POST区别

  1. 数据传输方式：GET请求通过URL传输数据，而POST的数据通过请求体传输。
  2. 安全性：POST的数据因为在请求主体内，所以有一定的安全性保证，而GET的数据在URL中，通过历史记录，缓存很容易查到数据信息。
  3. 数据类型：GET只允许 ASCII 字符，而POST无限制
  4. GET无害：刷新、后退等浏览器操作GET请求是无害的，POST可能重复提交表单
  5. GET只读，不引起服务器状态变化且幂等。POST可能引起资源修改且非幂等。
  此处幂等：多个请求返回相同的结果。
  HTTP请求四个方法：PUT增，DELETE删，POST改，GET查

### RESTful架构

  REST全程：资源的表现层状态转化

  1. 资源：网络上的一个实体，前端需要请求到的东西，每个资源对应一个特定的URI；
  2. 表现层：把资源呈现出来就叫做它的表现层，如文本用html/json格式表现，客户端和服务器之间传递资源的某种表现层；
  3. 状态转化： 客户端和服务器通过http协议互动，HTTP协议是无状态协议，所有状态保存在服务器端，客户端通过GET、POST、PUT、DELETE操作方式操作服务端资源进行状态转化。

### http状态码

1XX：信息状态码
  > 100 Continue 临时回应，表示客户端请继续。

2XX：成功状态码
  > 200 OK 请求成功，正常返回信息
  > 201 Created 请求成功并且服务器创建了新的资源
  > 202 Accepted 服务器已接受请求但尚未处理

3XX：重定向，请求目标有变化
  > 301 Moved Permanently 资源已永久移动到新位置。以后应使用资源新的URI。
  > 302 Found 资源已被临时性重定向。希望用户本次使用新的URI。
  > 303 See Other 同302，客户端应当采用get方法获取资源。
  > 304 Not Modified 请求的网页未修改过。

4XX：客户端错误
  > 400 Bad Request 服务器无法理解请求的格式，客户端不应当尝试再次使用相同的内容发起请求。
  > 401 Unauthorized 请求未授权。
  > 403 Forbidden 被服务器拒绝访问。
  > 404 Not Found 找不到如何与 URI 相匹配的资源。

5XX: 服务器错误
  > 500 Internal Server Error 服务器端在执行请求时发生了错误。
  > 503 Service Unavailable 服务器端暂时无法处理请求，可一会再试。

### 跨域请求

产生跨域是因为浏览器同源策略（同源：域名+协议+端口；两个不同的域名指向同一个ip地址，是非同源）

1.JSONP： script 标签的 src 属性不会被同源策略所约束，可以获取任意服务器上的脚本并执行。请求需要带callback，返回的json数据被callback包裹。

```javascript
    // 1
    var script = document.createElement('script');
    script.type = 'text/javascript';
    script.src = 'http://www.domain2.com:8080/login?user=admin&callback=onBack';
    document.head.appendChild(script);
    function onBack(res) {
        alert(JSON.stringify(res));
    }
    // 2
    $.ajax({
        url: 'http://www.domain2.com:8080/login',
        type: 'get',
        dataType: 'jsonp',
        jsonpCallback: "onBack",
        data: {}
    });
    // 3
    this.$http.jsonp('http://www.domain2.com:8080/login', {
        params: {},
        jsonp: 'onBack'
    }).then((res) => {
        console.log(res);
    })

    //后台
    onBack({"status": true, "user": "admin"});
```

2.跨域资源共享（CORS）

浏览器对跨域请求区分为“简单请求”与“非简单请求”

- 简单请求：1、请求方法为head/get/post/；2、且HTTP头部信息包含在Accept | Accept-Language | Content-Language | Last-Event-ID | Content-Type:application/x-www-form-urlencoded、 multipart/form-data、text/plain
- 非简单请求：不满足上述1&2，如content-type=applicaiton/json , method = PUT/DELETE...。
- 浏览器判断跨域为简单请求的时候，会在Request Header中添加 Origin（协议/域名/端口）字段 ，表示请求源，CORS服务端将该字段作为跨源标志，验证通过会在Response Header 添加Access-Control-Allow-Origin等字段。
- 浏览器判断跨域为非简单请求的时候，首先发出OPTIONS预检请求，服务端处理后对Response Header添加Access-Control-Allow-Origin等验证字段，客户端接受预检请求的返回值进行请求预判断，验证通过后，主请求发起。非简单请求需要CORS服务端对OPTIONS类型的请求做处理，其他与简单请求一致。

- 前端：若要携带cookie前端设置withCredentials = true；
- 后端：

    ```js
      response.setHeader("Access-Control-Allow-Origin", "http://www.domain1.com"); // 允许跨域访问的域名（协议+域名+端口）
      response.setHeader("Access-Control-Allow-Credentials", "true"); // 允许前端带认证cookie：启用此项后，上面的域名不能为'*'，必须指定具体的域名
      response.setHeader("Access-Control-Allow-Headers", "Content-Type,X-Requested-With");// 提示OPTIONS预检时，后端需要设置的两个常用自定义头
    ```

3.nginx反向代理接口跨域；真实部署的时候用，修改nginx.conf文件，location匹配要代理的接口，proxy_pass代理到真正的域名下
4.Nodejs中间件代理跨域 http-proxy-middleware；开发的时候用，结合3 + 4，请求先到node服务，然后再转发到实际请求地址，先走路由，后根据路由匹配到对应的controller，在controller中去请求实际接口。

5.HTML5 API postMessage()：页面和其打开的新窗口的数据传递，页面与嵌套的iframe消息传递，多窗口之间消息传递。
6.WebSocket协议跨域：浏览器与服务器全双工通信，允许跨域通讯。
7.window.name + iframe； location.hash + iframe； document.domain + iframe

### 前端安全

1. 跨站脚本XSS，没有对用户的输入进行严格的限制，使得攻击者可以上传恶意脚本。
2. 跨站请求伪造CSRF

### 前端即时通讯

1. 短轮询
2. Comet技术：基于 HTTP 长连接、无须在浏览器端安装插件的“服务器推”技术，在客户端和服务端需要三方库支持。
   - 长轮询的方式在每次请求时，服务器端会保持该连接在一段时间内处于打开状态，而不是在响应完成之后就立即关闭。
   - 这样做可以在连接处于打开状态的时间段内，服务器端产生的数据更新可以被及时地返回给浏览器。
   - 当上一个长连接关闭之后，浏览器会立即打开一个新的长连接来继续请求。
3. SSE（Server-sent Events）：服务器端与浏览器端之间的通讯协议 + 浏览器端可供 JavaScript 使用的 EventSource 对象。
4. WebSocket：在服务器端和浏览器之间建立一个套接字连接，可以进行双向的数据传输。开源工具Socket.io。

### 事件委托

事件委托是利用js事件冒泡的特性，将内层元素的事件委托给外层处理。

### typeof

 typeof共会返回七种类型：number, boolean, string, undefined, object, function, symbol

### 从输入url到页面加载完成发生了什么

1、浏览器的地址栏输入URL并按下回车；

2、浏览器查找当前URL是否存在缓存，并比较缓存是否过期；

3、DNS解析URL对应的IP；

4、根据IP发出HTTP(S) 请；

5、服务器处理请求，浏览器接收HTTP响应；

6、解析HTML，解析css，渲染DOM树，加载js资源；

创建DOM树时：

1. 浏览器将接收到的二进制数据按照指定编码格式转化为HTML字符串。
2. 浏览器将HTML字符串通过HtmlDocumentParser解析成Tokens（一个token就是一个标签文本的序列化）。HtmlTreeBuilder对token进行分类处理（标签、属性、文本、换行等）
3. 对Node添加属性，根据去节点自带的指针确定其父子兄弟关系。
4. 构建出DOM Tree。

<https://www.cnblogs.com/jin-zhe/p/11586327.html>

### 线程、Event Loop、同步、异步

数据结构：

1. 堆（Heap）：利用完全二叉树维护的一组数据，是线性数据结构，一棵倒过来的树，每个结点都有一个值，堆的存取是随意的。
2. 栈（Stack）：限定仅在表尾进行插入或删除操作的线性表，先进的数据被压入栈底，后进的数据在栈顶，读数时从栈顶弹出数据。
3. 队列（Queue）：允许在表后端（队尾）插入，在表的前端删除的线性表。

线程：操作系统能够进行运算调度的最小单位。

单线程：所有任务需要排队，前一个任务结束，才会执行后一个任务。

js任务：

1. 宏任务：script代码、setTimeout、setInterval、I/O、UI render
2. 微任务：promise.then、Object.observe(已废弃)、MutationObserver

js单线程不阻塞的机制：Event Loop：

1. 任务进入执行栈等待主线程执行；
2. 判断同步任务与异步任务；
3. 同步任务在执行栈中按照顺序等待主线程依次执行；
4. 异步任务在有了结果后，将注册的回调函数放入任务队列中等待主线程空闲（执行栈被清空），被读取到栈内等待主线程的执行；
5. 执行栈执行结束，进入任务队列，先检查微任务队列，执行并清空微任务队列后执行下一个宏任务；
6. 每次单个宏任务执行完毕后，检查微任务队列是否为空，如此循环.

script：HTML解析 - 加载js - 执行js - HTML解析
script&defer：HTML解析 + 异步加载js - HTML解析结束后执行js
script&async：HTML解析 + 异步加载js - 加载完js后立即执行js - 解析HTML

### 不可变数据

1. 浅复制 Object.assign、... ，只能复制一层,在多层嵌套的情况下依然会出现副作用。
2. 深克隆：考虑正则、数组、Date、Symbol、特殊类型、原型链、循环引用等，实现繁琐，在生产环境中用lodash的深克隆实现。但性能开销较大。
3. 兼容性能和效果：immutable.js、immer不可变数据库。

### 登录token验证

雅典娜登录验证：
预登陆用户id+验证码，获取随机码loginRandom和盐salt，而后进行登录用户id+密码，密码为MD5加密的用户密码并加盐和随机码。

基于session的用户认证：
登录成功后，服务端生成用户相关的session数据，将sessionID发送给浏览器，在响应头中带着set-cookie='connect-sid'，客户端会把信息种植到本地的cookie中，且是httponly的形式，
下次客户端发起请求时直接携带上cookie中的sessionID以此验证，验证成功后返回数据。

基于token的用户认证：
登录成功后，服务器生成token，通过base64编码将token返回给客户端。客户端将token保存起来，下次请求时带着token，服务器收到后验证token，验证成功后返回数据。

### 项目中用的es6新特性

1. let与 const：
   - let声明变量，有块级作用域，不可重复声明，不存在变量提升。
   - const声明常量，声明后必须赋值，必须为不可变的量。
   - let、const、class声明的全局变量不属于顶层对象的属性。
   - 暂时性死区：
2. 箭头函数this指向定义时所在对象，不能作构造函数，不存在arguments对象，不能用作Generator函数。
3. 数据结构Set：类似于数组，成员不能重复，可遍历。
   - 实例方法：add(value)、delete(value)、has(value)、clear()
   - 转为数组：Array.from(set)、[...set]
   - 遍历方法：keys()、values()、entries()
4. 数据类型Map：类似于对象，键值对的集合，键不受限。
   - 实例方法：set(key, value)、get(key)、has(key)、delete(key)、clear()
   - 遍历方法：keys()、values()、entries()
5. Async/Await
6. 解构赋值
7. 对象属性的简洁表示法
8. 对象合并：Object.assign(目标,源)，将源对象所有可枚举属性，浅拷贝到目标对象。
9. ES6实现继承：利用extends与super实现子类继承
声明-解构赋值-字符串扩展-数值扩展-对象扩展-数组扩展-函数扩展-Symbol-Set-Map-Proxy-Reflect-Class-Module-Iterator-Promise-Generator

### for循环 、 forEach 、for in 、for of

- forEach相对for循环简洁，但中途无法跳出循环，continue break return都不奏效。
- for(let key in obj){} 为遍历对象而设计，循环读取键名，可以遍历出对象继承的属性，即原型链上的key，可通过hasOwnProperty方法判断一个对象自身是否含有某个属性。若遍历数组，key为字符串‘1’、‘2’。
- for(let value of obj){} ES6新增所有数据结构的统一遍历方法，循环读取键值。可以与continue break return配合使用。
- for...of适用于所有部署了[Symbol.iterator]属性的数据结构，如Map，Set，Array，类似于数据的对象arguments、DOM Nodelist等。

### 遍历对象属性

- for(let key in obj){} 包括原型链上的对象继承的-可枚举-属性
- object.keys 不包括原型链上的-可枚举-属性
- object.entries 不包括原型链上的-可枚举-属性
- object.getOwnPropertyName 不包括原型链上的-可枚举+不可枚举-属性

### 数组的方法，哪些会改变原数组

- push()，尾加，返回修改后数组的长度，-------改变原数组
- pop()，尾减，返回移除项，-------改变原数组
- shift()，头减，返回移除项，-------改变原数组
- unshift()，头加，返回修改后数组的长度，-------改变原数组

- reverse()，反转排序，-------改变原数组
- sort()，排序，-------改变原数组

- concat()，合并且创建新数组
- slice(起始位置,结束位置)，截取包头不包尾，创建新数组，-------改变原数组
- splice(删除的第一项的位置,删除的项数,插入的项)，改变原数组

- forEach()对数组中的每一项运行给定函数。这个方法没有返回值
- every()对数组中的每一项运行给定函数，如果该函数对每一项都返回true，则返回true
- some()对数组中的每一项运行给定函数，如果该函数对任一项返回true，则返回true
- filter()对数组中的每一项运行给定函数，返回该函数会返回true的项组成的数组
- map()对数组中的每一项运行给定函数，返回每次函数调用的结果组成的数组
- entries()，keys() 和 values(),返回遍历器对象，用for…of遍历

- Array.from()将类似数组的对象和可遍历对象转为数组
- Array.of(3) //[3];  Array.of(3, 4, 5) //[3, 4, 5]; 比较Array(3) //[, , ,]; Array(3, 4, 5) //[3, 4, 5]
- find() 和 findIndex()，返回数组中第一个满足条件的元素/位置，如果没有则返回undefined/-1
- ['a', 'b', 'c'].fill(填充值, 填充起始位置, 填充结束位置)
- [1, 2, 3].includes(包含谁, 从哪开始找)
- [1, 2, [3, [4, 5]]].flat(拉平多少层/默认“拉平”一层/Infinity拉全部) 数组降维
- [1, 2, 3, 4, 5].copyWithin(被开始替换, 开始读取，停止读取)，在数组内部将指定位置成员覆盖到其他位置，修改当前数组。，-------改变原数组
- ['a', 'b', 'c'].fill(填充值, 填充起始位置, 填充结束位置)，-------改变原数组
- entries()、keys()、values()返回遍历器对象，可用 for...of 遍历

### Promise

- Promise：异步编程的一种解决方案
- 优势：可以将异步操作以同步操作的流程表达出来，避免了层层嵌套的回调函数。此外，Promise对象提供统一的接口，使得控制异步操作更加容易。
- Promise构造函数接受一个函数作为参数，该函数有两个参数resolve函数和reject函数，
- resolve函数在异步操作成功时将异步操作的结果作为参数传递出去，resolve(res)调用触发then方法第一个参数的回调函数。
- reject函数在异步操作失败时将异步操作报出的错误作为参数传递出去。reject(msg)调用触发then方法第二个参数的回调函数。
- Promise实例then方法接受两个回调函数作为参数，第一个回调函数是Promise对象的状态变为resolved时调用，第二个回调函数是Promise对象的状态变为rejected时调用。

```javascript
const promise = new Promise(function(resolve, reject) {
  if (true/* 异步操作成功 */){
    resolve(value);
  } else {
    reject(error);
  }
});
promise.then(function(value) {
  // success
}, function(error) {
  // failure
});
```

- Promise.all：接受一个数组作为参数，将多个Promise实例包装成一个新的Promise实例。成功返回结果数组，失败返回最先被reject失败状态的值。
- Promise.race：接受一个数组作为参数，哪个结果获得的快，就返回那个结果，不管结果本身是成功状态还是失败状态。
- Promise.resolve：接受一个对象参数，将现有对象转为 Promise 对象。

原生js实现ajax：建XMLHttpRequest、open、onreadystatechange、 send


### Generator

Generator 函数是 ES6 对协程的实现。

协程：一种程序运行的方式，可以理解成“协作的线程”或“协作的函数”。
多个函数可以并行执行，但是只有一个函数处于正在运行的状态，其他函数都处于暂停态，函数之间可以交换执行权。
也就是说，一个函数执行到一半，可以暂停执行，将执行权交给另一个函数，等到稍后收回执行权的时候，再恢复执行。

Generator 函数是一个异步的封装，异步操作需要暂停的地方用 yield 语句标明。

定义 function、*、yield ：

```javascript
function* name() {
  yield 'hello';
  yield 'world';
  return 'ending';
}
var hw = name();
hw.next();// { value: 'hello', done: false }
hw.next();
```

Generator 函数调用时返回一个遍历器对象，调用遍历器对象的next方法，分段执行Generator，返回当前阶段的value和done。

yield表达式用来暂停执行，next方法用来恢复执行。

### Async/Await

Async函数是Generator函数的语法糖，将 Generator 函数的星号（*）替换成async，将yield替换成await。

Async 函数调用时返回一个Promise对象，
Await—在async函数内部使用，在Promise前使用，暂停异步的功能执行，直到Promise完成并返回结果。解决异步编程的麻烦。

### 算法

时间复杂度S(n)：算法执行时耗费时间的长度。
时间复杂度量级：

- 常数阶O(1)：无论数据规模n如何增长，计算时间是不变的。
- 对数阶O(logn)：计算时间随数据规模n对数级增长，如二分查找法，循环成2倍数缩减搜索范围。
- 线性阶O(n)：计算时间随数据规模n线性增长，如一层循环。
- 线性对数阶O(nlogn)：如归并排序。
- 平方阶O(n²)：如冒泡排序，双重循环。
空间复杂度T(n)：算法执行时占用存储单元的长度。

排序算法: 冒泡排序、希尔排序、归并排序、快速排序

数据结构指的是对象在计算机中的一种逻辑结构，对数据对象的操作所用的方法就是算法。

## 框架与项目

### webpack搭建项目

配置过程：

1. 初始化package.json：npm init
2. 安装 webpack、webpack-cli(使可在命令行中使用webpack命令)、webpack-dev-server(热重载)、vue
3. 创建文件：src-根模板app.vue，入口文件index.js；编译文件webpack.config.js
4. webpack.config.js
   - mode：production打包文件自动压缩；development不压缩，默认开启sourceMap
   - entry：入口文件path
   - output：输出文件filename和path
   - resolve：解析模块路径的相关策略配置，
      - resolve.extensions：当引入一个文件没有扩展名时，会依据此配置从左到右匹配。
      - resolve.alias：为初始模块路径创建别名。
   - module：编译模块
      - 编译.vue文件：vue-loader、vue-template-compiler、VueLoaderPlugin(将定义的其它规则复制并应用到 .vue 文件里相应语言的块)
      - 编译css：
         - style-loader：拦截style标签
         - css-loader：编译css
         - stylus-loader：编译预处理器
         - postcss-loader + autoprefixer：添加浏览器兼容前缀，建postcss.config.js文件，引入autoprefixer插件
      - 编译图片：url-loader(可转base64)、file-loader
      - 编译ES6：
         - babel-core、babel-loader
         - babel-preset-env(设置编译规范)
         - babel-polyfill(新语法兼容处理) 或 babel-plugin-transform-runtime + babel-runtime(避免全局变量污染)
         （参考：<https://zhuanlan.zhihu.com/p/35378233>）
   - optimization:{usedExports:true, splitChunks:{chunks: 'all'}},开发环境tree shaking和全部默认code splitting
   - plugins：
      - HtmlWebpackPlugin：打包结束后自动生成HTML，并把打包生成的js文件引入到HTML中
      - HotModuleReplacementPlugin：开启webpack-dev-server的HMR(模块热更新，局部刷新)
      - MiniCssExtractPlugin：css默认直接打包进js文件，此插件可提取出css文件
      - OptimizeCssAssetsPlugin：压缩css
      - DefinePlugin：允许创建一个在编译时可以配置的全局常量。对开发和生产构建不同行为有用
   - devServer：本地服务host、port、open、proxy，只有通过webpack-dev-server启动webpack时，配置devServer才会生效。
   - devtool：配置sourceMap映射关系
      - 开发环境：cheap-module-eval-source-map，生产环境：cheap-module-source-map
      - eval：打包后文件被eval执行，追加sourceUrl指向原文件
      - source-map：为打包文件生成map文件，通过一个DataURL映射
      - cheap：忽略列，只包含行位置信息
      - module：对loader或三方模块进行映射
      - 调试vue组件：debugger和devtool:'#eval-source-map';浏览器插件vue devtool
   - 启动执行：npm run执行package.json中可执行脚本scripts命令：
        - 配置执行命名：用wepack执行webpack.config.js，开发环境用webpack-dev-server执行文件启动热重载
        - 配置环境变量：cross-env(运行跨平台设置和使用环境变量的脚本)、NODE_ENV=dev
        - 获取环境变量：DefinePlugin、process.envNODE_ENV.

 执行流程：

 1. 初始化参数：读shell语句和配置文件获取参数；
 2. 开始编译：依据参数初始化 Compiler 对象；
 3. 确定入口：依据配置找到入口文件；
 4. 编译模块：从入口出发调用loader编译文件；
 5. 编译完成：得到每个每个模块编译后内容和依赖关系runtime和manifest；
 6. 输出资源：chunk转为文件加入输出列表；
 7. 输出完成：根据配置指定文件名和路径写入系统。
 8. 其中：插件监听事件执行特定任务。

- Loader：帮助我们处理模块，让webpack拥有加载和解析非JS文件的能力。
  - 原理：loader是一个函数，可以获取到源文件内容，然后对源代码进行处理，最后返回回去。
- Plugin：扩展webpack功能，打包的时候在某个具体时刻，做一件事情，改变输出结果。
  - 和新机制是事件驱动，事件钩子里面定义了一些具体的时刻值
- Babel：现代 JS 语法转换器。
  - 解析: 将代码(其实就是字符串)转换成 AST( 抽象语法树)
  - 转换: 访问 AST 的节点进行变换操作生成新的 AST
  - 生成: 以新的 AST 为基础生成代码

### 白屏、webpack性能优化。项目开发优化

白屏原由：

1. webpack打包的项目，会出现很多体积大的 chunk，影响加载速度。
2. 浏览器同一域名并发请求的限制阻塞问题；
3. 网络、带宽。

项目优化：

1. 体验优化：好的loading可以提升用户体验；
2. 体验优化：使用Skeleton Screen骨架屏提升用户感知体验；
3. 创建DOM耗时：服务端渲染SSR，直接返回的 HTML 就是带完整 DOM 结构，省去js执行创建dom的工作；

4. 加快网络传输：开启http2；
   - 多路复用：允许同时通过单一的 HTTP/2 连接发起多重的请求-响应消息，单连接多资源减少网络拥塞；
   - 二进制分帧：在应用层和传输层之间增加二进制分帧层，将传输的信息分割为更小的二进制编码，减少传输量；
   - 支持首部压缩；
   - 支持服务端推送。

5. 开启浏览器缓存：
   - 在前端HTML页面的Meta标签和服务器HTTP协议头中定义；
   - 仅针对get请求，POST请求不会被缓存；
   - 客户端请求资源-*新鲜度*检测-如在过期时间内-取浏览器缓存200 form catch；-如已经过期-服务器根据校验值再验证-如验证通过-返回304 not modified资源未修改，读取浏览器缓存；-如验证未通过-资源已过期或者修改-获取新内容。
   - 设置新鲜度：
     1. 强缓存：Expires: 设定过期具体时间
     2. 强缓存：Cache-Control: no-cache先缓存本地+校验新鲜度后使用、max-age控制过期时间
     3. 协商缓存：Last-Modified: 告诉浏览器当前资源的最后修改时间
     4. 协商缓存：If-Modified-Since: 告诉服务器当前资源的浏览器所知道的最后修改时间
   - 设置校验值：
     1. ETag：告知浏览器当前资源的唯一标识符
     2. If-None-Match: 告知服务器当前资源浏览器所知道的唯一标识符。

6. webpack配置控制请求资源加载提速：
    - code splitting 代码分割：
       - 抽离第三方库，将应用基础库和特定依赖的库分离，控制没有必要在首屏加载的文件，减小请求js的体积，防止阻塞；
       - 内置插件SplitChunksPlugin：在production模式下默认开启，只作用于异步chunk，可设置optimization.splitChunks.chunks = 'all';
       - 内置默认分割规则：新bundle被两个及以上模块引用或来自node_modules；新bundle压缩前大于30kb；异步并发加载bundle不能大于5个；初始加载bundle不能大于3个；
       - 特殊需求：optimization.splitChunks API配置
          - 如何分chunk？那些库分在一个chunk？如何取舍？有什么坑？怎么解决？
    - 利用缓存：
       - hash：每次构建项目都会发生改变，无法缓存。
       - chunkhash：不同chunk生成不同hash，通常做法是把公共依赖库和入口文件隔离并单独打包构建，文件名以chunkhash标识，只要依赖公共库不变，chunkhash就不变，从而达到缓存的目的。
       - contenthash：依据文件内容产生不同的hash，通常做法是把项目中css抽离出对应文件，文件名以contenthash标识，即使所属的chunk改变了，只要css不变contenthash就不变，实现缓存。
    - Tree Shaking 剔除无用代码，减小体积：
      1. 配置：webpack4生产环境自动生效，开发环境配置:optimization:{usedExports:true,sideEffects: true}
      2. 原理：
         - Tree Shaking 依赖于es6的静态导入导出(import/export)。打包时会通过import确定引用包的export导出的某一个变量之一，在告知没有副作用的情况下，删除掉没有用到的其他导出代码。
         - 静态导入是指一开始就默认加载这个文件，而不是一步一步执行代码判断逻辑，去导入对应文件。
      3. 副作用
         - 副作用: 在导入时会自行运行一段函数，从而改变了 window 变量啊或者其他的变量以供导入的包能正常运行，而不是只单单 export 了变量。
         - sideEffects配置告诉webpack识别sideEffects标志的package.json或规则以跳过模块，这些模块在未使用导出时被标记为不包含副作用， 则可以把无副作用的未使用的导出进行删除。
         - package,js -- sideEffects:["@babel/polyfill", "*.css"]，告诉编译器该模块is pure，可以进行无用模块删除。
      4. 使用：Tree Shaking只依据ES6模块查找，但Babel默认把模块转译成CommonJS模块，设置不对ES6模块进行处理：.babelrc->presets:['env', {modules: false}]
    - 优化 SourceMap，开发环境推荐：cheap-module-eval-source-map，生产环境推荐：cheap-module-source-map；

7. 路由懒加载：
    - vue异步组件：resolve => require(['@/components/home'],resolve)；
    - es->import()：import(/*webpackChunkName: 'ImportFuncDemo'*/ '@/components/home')，同webpackChunkName会合并打包成一个js文件；
    - webpack->require.ensure()：require.ensure([], () => r(require('@/components/home')), 'demo')，同chunkName会合并打包成一个js文件。

8. 组件懒加载：路由内进行组件级别拆分，按需加载；
9. 组件预加载：组件懒加载的弊端，未加载的组件在触发加载当下会有等待时间，可在适当的时机给与预加载；
10. keep-alive组件缓存：路由配置/标签包裹，在页面已经跳转后依然不销毁组件,在内存中保存组件对应的实例，再次需要渲染的时候可以利用此缓存。适当手动销毁释放内存；

11. 基础代码优化：
    - 尽量使用v-if，减少dom数量，加快初始渲染。预渲染需求/频繁切换显示状态/有权限限制情况下使用v-show；
    - 不在模板里面写过多的表达式与判断，存在methods和computed中；
    - v-for必须加上key，作为当前dom节点唯一标识id，当数据发生变化时key相同会复用这个节点提高dom更新效率，不将有改变index交互的列表使用index作为key；
    - 提取css文件：全局通用样式、覆盖浏览器默认样式、复写Element样式；
    - 长列表性能优化：纯粹展示的数据通过Object.freeze冻结，禁止Vue劫持数据，减少组件初始化时间；
    - 绑定在组件之外的事件手动销毁，避免内存泄漏；
    - 使用的第三方库按需引入所需部分import{ Button, Select } from'element-ui'；
    - html标签不要有太深层次的嵌套，css选测器编写适当，加快浏览器解析，优先加载css，避免阻塞的js加载。

12. 其他：图片懒加载方案；代码压缩；雪碧图；
13. 使用 Chrome Performance 查找性能瓶颈。

### webpack5

### 大批量数据前端展示卡顿问题

 1. 使用函数节流和防抖，避免短时间内多次触发复杂的业务逻辑而造成页面卡顿，节约性能。
    节流：n秒内多次触发事件只执行第一次：在window.onresize事件中做节流处理，防止频繁调整浏览器窗口大小导致崩溃。
    防抖：在事件被触发n秒后再执行回调，如果在这n秒内又被触发，则重新计时。用于input输入框架的格式验证；高频点击提交事件；拖拽、滚动等频繁事件。
 2. 使用 axios 的 canceltoken 取消请求（通过执行abort中断已发送的请求，客户端不再接收数据），上一级路由返回的数据不再走回调函数，也不会在页面上显示不必要的数据了。
 3. 节点优化，避免过多无用的节点，不渲染全部数据，只对「可见区域」进行渲染，进行局部渲染和 DOM 回收。不将全部数据与dom绑定，只将局部可视区数据绑定在节点上，通过监听事件替换数据。
 4. 大量数据渲染：虚拟列表。
 5. 点击数据大的组件Echarts绘图很多数据，但切换其他组件统计图时，出现了卡顿，echarts实例占用内存，在beforeDestroy的时候dispose释放示例的资源。
 6. 大量数据的计算：Web Worker。当一段脚本长时间占用着处理机，就会挂起浏览器的GUI更新，主线程不要长时间执行大量数据。
 7. vue中纯粹展示的数据通过Object.freeze冻结，禁止Vue劫持数据，减少组件初始化时间
 8. 不要在一个 vue 组件上绑定那么多的元素，请拆分成多个子组件，缩小更新范围。表单复杂的多，比对的层级深

### webpack 与 gulp

- Webpack是基于模块化打包的工具，把一切当成模块
- Gulp是基于任务运行的工具，自动执行指定的任务，就像流水线，把资源放上去然后通过不同插件进行加工

### 雅典娜打包效率提升

webpack之DllPlugin：分离第三方库，每次项目代码更改，只会打包业务代码，节省了三方库的打包时间，打包速度更快。

1. 创建webpack.dll.conf.js文件定义DllPlugin打包规则，最终将三方库打包成vendor.dll.js并放在特定的目录下，且创建出映射文件vendor-manifest.json
2. 在webpack.config.js引入插件DllReferencePlugin，配置manifest:引入上述vendor-manifest.json
3. 在html页面里手动引用vendor.dll.js
4. 更新三方模块时重新执行脚本 "dll": "webpack --config ./webpack.dll.config.js"

webpack性能优化：

1. 安装新版本 node npm等；
2. 在尽可能少的模块上应用loader，缩小作用范围，减少无畏的代码分析；
3. 尽可能少的使用plugin、官方推荐的性能好的；
4. 合理的配置resolve参数减少查找；
5. 使用DllPlugin提高打包速度；
6. 控制包文件大小tree shaking、splicechunks；
7. 借助插件happypack实现多线程打包提高速度；
8. 合理使用sourceMap；
9. 分析打包结果针对性优化；
10. 开发环境打包使用webpackDevServe,内存读取比硬盘读取快的多;
11. 开发环境调试不需要代码压缩，mode设置为development。

### vue生命周期

Vue实例从开始创建、初始化数据、编译模版、挂载Dom -> 渲染、更新 -> 渲染、卸载等一系列过程称为Vue的生命周期。

创建前/后：beforeCreate、created
载入前/后：beforeMount、mounted
更新前/后：beforeUpdate、updated
销毁前/后：beforeDestroy、destroyed
activited：keep-alive 组件激活时调用
deadctivated：keep-alive 组件停用时调用

在生命周期中首先创建一个vue实例，

- 初始化生命周期和事件：initLifecycle(vm) -> initEvents(vm) -> initRender(vm) -> 执行beforeCreate钩子，拿不到实例里的任何东西。
- 依赖注入导入依赖项：initInjections(vm)初始化vue实例的inject -> initState(vm):props、methods、data、watch、computed等数据初始化-> initProvide(vm)赋值到当前实例上 -> 执行created钩子。可异步数据获取、对实例数据进行初始化操作。
- 检查实例的el(Vue实例的挂载目标)项是否存在，存在则继续检查template项，不存在则手动绑定调用vm.$mount()后检查template项。
- 如有template将其编译到render函数中，没有则将el外部HTML作为template编译，生成编译好的模板字符串，-> 执行beforeMount钩子。
- 将内存中编译好的模板映射到页面中去， -> 执行mounted钩子，此时可直接操作dom。
- 当data被修改，执行beforeUpdate钩子。data是新的，页面是旧的。
- 虚拟DOM重新渲染并应用更新，执行updated钩子。
- 调用$destroy函数时，执行beforeDestroy。实例属性均可用。
- 销毁完毕，执行destroyed钩子。

父组件监听子组件生命周期：

```html
  <!--1.自组件在mounted中this.$emit("mounted");-->
  <Child @mounted="doSomething"/>
  <!--2.@hook直接可监听生命周期事件-->
  <Child @hook:mounted="doSomething" ></Child>
```

React的请求放在：componentDidmount生命周期中

### vue：computed和watch

computed： 计算属性，进行数值计算,且依赖于其他数据，把这个数据设计为computed，其值会被保存，当依赖发生改变时下一次获取时才会重新计算。

watch： 观察作用，类似于某些数据的监听回调 ，每当监听的数据变化时都会执行回调进行后续操作；

### vue自定义指令directive

对普通 DOM 元素进行底层操作。
钩子函数

- bind：只调用一次，指令第一次绑定到元素时调用。
- inserted：被绑定元素插入父节点时调用。
- update：所在组件的 VNode 更新时调用。
- componentUpdated：指令所在组件的 VNode 及其子 VNode 全部更新后调用。
- unbind：只调用一次，指令与元素解绑时调用。

钩子函数参数

- el：指令所绑定的元素，可以用来直接操作 DOM 。
- binding：（只读）对象包含属性：
  - name：指令名，不包括 v- 前缀。
  - value：指令的绑定值。
  - oldValue：指令绑定的前一个值。
  - expression：字符串形式的指令表达式。
  - arg：传给指令的参数。
  - modifiers：一个包含修饰符的对象。

### vue 指令有哪些

 1. v-text:更新元素的 textContent
 2. v-html:内容按普通 HTML 插入 - 不会作为 Vue 模板进行编译
 3. v-show:切换元素的 display CSS
 4. v-if:有条件地渲染元素,销毁并重建
 5. v-else/v-else-if
 6. v-for:基于源数据多次渲染元素
 7. v-on:绑定事件监听器
 8. v-bind:动态地绑定一个或多个 attribute
 9. v-model:用于表单控件绑定
 10. v-slot:提供具名插槽或需要接收 prop 的插槽,2.6+版本启用
 11. v-cloak:保持所在元素不显示，直到编译结束
 12. v-once:只渲染元素和组件一次

### Vue组件通信

1. props/$emit+v-on: 父->子props向下传递，子->父$emit向上派发事件；
2. EventBus: 俩组件无关系：通过EventBus进行信息的发布与订阅；
3. vuex: 通过vuex管理全局的数据流；
4. $attrs/$listeners: Vue2.4中加入的$attrs/$listeners可以进行跨级的组件通信；
5. provide/inject：由祖先组件提供了一个provide，provide里的属性可供所有的后代组件通过inject注入并调用，这成为了跨组件通信的基础；
6. 通过solt插槽或者ref实例进行通信。

EventBus事件总线：一种发布订阅设计模式，通过解耦发布者和订阅者简化事件传递。

1. class初始化EventEmeitter，创建事件清单；
2. EventEmeitter.prototype.emit，从事件清单中获取对应事件的回调函数，触发事件；
3. EventEmeitter.prototype.addListener，监听回调函数，追加事件到事件清单中；
4. 实例化 const emitter = new EventEmeitter()；
5. 触发事件：emitter.emit('myfn', '参数')；
6. 监听事件：emitter.addListener('myfn', can => {console.log(can);});

vue的单项数据流：
> 所有的 prop 都使得其父子之间形成了一个单向下行绑定。
> 父级数据更新会向下流动到子组件中，但是反过来则不行。这样会防止从子组件意外改变父级组件的状态。
> 子组件不应该在内部改变prop，只能通过 $emit 派发一个自定义事件，父组件接收到后，由父组件修改。

react组件通信：

 1. 父子组件,父->子直接用Props,子->父用callback回调
 2. 非父子组件,用发布订阅模式的Event模块
 3. 项目复杂的话用Redux、Mobx等全局状态管理管库

### vuex与浏览器缓存，vuex刷新后数据没了

1. 存缓存可修改可知道存了什么，不会自动清空数据
2. 刷新浏览器vuex会被重置，存缓存不会，比如token可存本地，用户权限数据可存vuex，出于安全存在vuex更合理，用户退出即消失
3. vuex 将数据存在对象树的变量中，vue 应用从变量中读取数据，页面关闭变量消失，刷新页面重新生成

### vue响应式系统、虚拟DOM

vue响应式系统：

1. 任何一个 Vue Component 都有一个与之对应的 Watcher 实例。
2. Vue 的 data 属性会被添加 getter 和 setter 属性。
3. 当 Vue Component render 函数被执行的时候, getter方法会被调用, 此时会进行依赖收集，记录此Vue component所依赖的所有data。
4. data 被改动时, setter方法会被调用, 此时所有依赖于此 data 的组件会调用他们的 render 函数进行更新。

虚拟DOM：Virtual DOM是更加轻量级的对DOM的抽象描述，本质上是一个是JavaScript对象，

起源：

1. 频繁操作DOM会造成浏览器的回流或者重绘影响性能，在patch过程中尽可能地一次性将差异更新到DOM中保证性能；
2. 省略手动DOM操作可以大大提高开发效率；
3. 虚拟dom本质上是js对象，可以实现更好的跨平台，如实现SSR。

实现：

1. 一个创建Virtual DOM的函数，接受一定的参数,再根据这些参数返回一个DOM的抽象对象；
2. 一个创建Virtual DOM Tree的函数，构造DOM树；
3. 一个将抽象对象转化为真实DOM的函数；
4. diff比较新旧DOM树超出差异并更新；
5. diff 是虚拟dom技术中的必要产物，将变化更新到真实的dom上，降低时间复杂度为o(n)
6. 而diff算法的必要性就是组件中watcher粒度的降低，每个组件会有一个对应的 watcher 对象，组件中有很多data，为了精确的知道一个组件中到底谁发生了变化而使用diff，lifecycle.js - mountComponent()
7. diff算法执行的时刻是在vue实例执行其更新函数的时候，它会对比上一次渲染结果oldVnode和新的渲染结果newVnode，这个过程就是patch，patch.js - patchVnode()
8. diff整个过程是一个深度优先，同层比较的一个策略，

### vue的实现

关于**框架**：
   > 框架的存在是为了帮助我们应对复杂度，而框架本身也会带来复杂度。
   > 问题在于所要解决的问题的内在复杂度与所使用的工具的复杂度进行对比。
   > 适当复杂度的框架解决相应复杂度的问题。取决于场景。

框架复杂度：

- 声明式的渲染功能，尽可能避免手动操作，状态变化的时候自动更新。
- 组件系统，将大型界面切分成小的可控单元。
- 客户端路由，一个URL对应到一个应用的状态。
- 大规模的状态管理，多人协作，多组件之间共享，高效运行。
- 项目维护性及构建工具

   主流框架：
   > React和Vue：只做状态到界面映射，以及组件。
   > Angular：它有自己的路由，这些都会包含在里面。
   > React和Vue有一个共同特点，它们都有各自的配套工具，核心虽然只解决一个很小的问题，
   > 但它们有生态圈及配套的可选工具，当你把他们一个一个加进来的时候，就可以组合成非常强大的栈，
   > 就可以涵盖其他的这些更完整的框架所涵盖的问题。使得在构建技术栈的时候有可弹性伸缩。

   1. 声明式渲染：
      - DOM应尽可能是一个函数式到状态的映射，所有的逻辑在状态的层面去进行，当状态改变的时候，视图层在框架帮助下自动更新到合理的状态。
      - Vue的编译器把模板编译成一个渲染函数。函数被调用的时候就会渲染并且返回一个虚拟DOM的树->描述当前界面所应处的状态。
      - 将虚拟DOM树交给一个patch函数，负责把这些虚拟DOM真正施加到真实的DOM上。
      - Vue自身的*响应式系统*侦测在渲染过程中所依赖到的数据来源，可精确感知数据源变动，根据需要重新渲染生成新的虚拟DOM树，新旧树对比，最终patch函数施加改动。
      - 在浏览器中js运算非常快，但DOM本身是非常缓慢，把耗费时间的操作放在纯粹的计算中去做，保证最后计算出来的需要实际接触真实DOM的操作是最少的。
      - Vue的*依赖追踪*通过ES5的Object.defineProperty方法实现的。
      - Vue会遍历数据对象的属性，然后进行属性转换。每一个属性会被转换为一个 getter 和一个 setter。
      - 同时每个组件会有一个对应的 watcher 对象，负责在当前组件被渲染的时候，记录数据上面的哪些属性被用到了。
      - 当某个数据属性被用到，触发 getter，这个属性就会被作为依赖被 watcher 记录下来。
      - 相应的数据变动时，就会触发 setter，通知数据对象对应数据有变化。
      - 通知对应的组件，其数据依赖有所改动，需要重新渲染，触发diff执行。
      - 对应的组件再次调动渲染函数，生成 Virtual DOM，实现 DOM 更新。

   2. 组件系统
      - 把UI结构映射到恰当的组件树。
      - 基于构建工具实现单文件组件, 在一个Vue文件里同时写 template, script 和 style。通过构建可以对这些单文件组件做更多的分析。
   3. 客户端路由
      - 让应用的URL和组件树的状态之间的一个映射关系对应起来。
      - 嵌套路由、重定向和别名、具名路由、多个平级路由出口、异步数据处理、跳转动画、复杂匹配规则、跳转规则限制、当前活跃链接、滚动条行为、懒加载
   4. 状态管理
      - 本质上就是把整个应用抽象为一个state-view-action的一个循环，State 驱动 View 的渲染，而用户对 View 进行操作产生 Action，会使State产生变化，从而导致 View 重新渲染。
   5. 构建工具vuecli：开箱即用的热重载，单文件组件懒加载。
   6. 构建工具vuecli：在webpack支持下，开箱即用的热重载，单文件组件懒加载。编译

### mvvm、双向数据绑定

- MVVM：Model-View-ViewModel

   1. Model层: 数据层，前端通过Ajax完成客户端和服务端业务 Model 的同步。在层间关系里，主要用于抽象出 ViewModel 中视图的 Model。
   2. View 层: 模板层，定义结构、布局、展示 ViewModel 层的数据和状态。不处理状态，负责数据绑定的声明、 指令的声明、 事件绑定的声明。
   3. ViewModel 层: 处理 View 层的具体业务逻辑。ViewModel 底层会做好绑定属性的监听，与View层做到双向数据更新。
   MVVM主要通过数据来显示视图层而不是操作节点，解决了MVC中大量的DOM操作使页面渲染性能降低，加载速度慢。
   双向数据绑定：从界面的操作能实时反映到数据，数据的变更能实时展现到界面。

- 实现双向绑定的方法：
   1. 基于脏值检查（angular.js）；
      - 解释：存储所有变量的值，每当可能有变量发生变化需要检查时，就将所有变量的旧值跟新值一一进行比较，不相等就说明检测到变化，需要更新对应视图。
      - 在指定事件触发后进入脏值检查，执行$digest()或$apply()，框架内部执行或显示调用。
   2. 基于数据劫持（如vue.js）；
      - 解释：利用Proxy或Object.defineProperty劫持对象的访问器,在属性值发生变化时我们可以获取变化,从而进行进一步操作；
      - 优势1：可以精确获知数据变化的内容，降低查找变化值的性能损耗；
      - 优势2：无需显示调用，直接可以通知变化并驱动视图。
   3. 基于发布者-订阅者模式（观察者模式）；
      - 一对多的依赖关系，多个对象（订阅者）同时监听同一对象（发布者）的数据状态变化。当一个对象的状态发生改变时，所有依赖于它的对象都将得到通知。
      - 发布者：
        - 一个对象：包含订阅的类型和相关订阅者；
        - 一个函数：添加新订阅者到对应订阅类型的订阅者数组中；
        - 一个函数：从数组中移除指定订阅者；
        - 一个函数：当发布者的某一状态改变时通知所有的订阅者，即遍历订阅者提供的方法；
      - 订阅者：一个函数：当发布者状态发生改变时通知所使用的的回调函数。
      - 中间渠道/调度中心：从发布者接收事件，向订阅者发布事件
      - 优点：解耦。

- 基于数据劫持+发布订阅模式实现双向数据绑定：
   1. 利用Proxy或Object.defineProperty生成数据监听器Observer针对对象或其属性进行"劫持",在属性发生变化后通知订阅者；
   2. 实现一个指令解析器Compile，解析模板中的Directive(指令)，收集指令所依赖的方法和数据,等待数据变化然后进行渲染；
   3. 实现一个Watcher，作为连接Observer和Compile桥梁,它将接收到的Observer产生的数据变化,并根据Compile提供的指令进行视图渲染,使得数据变化促使视图变化.

- Proxy在目标对象之前架设一层“拦截”，外界对该对象的访问，都必须先通过这层拦截。
- Proxy相比Object.defineProperty的优势：
   1. Proxy可以直接监听对象而非属性；
   2. Proxy可以直接监听数组的变化；
   3. Proxy的多种拦截方法：除了get和set外，apply、ownKeys、deleteProperty、has、getOwnPropertyDescriptor、getPrototypeOf等Object.defineProperty不具备；
   4. Proxy返回的是一个新对象,可只操作新对象达到目的，Object.defineProperty是遍历对象属性直接修改；

### react与vue的区别和特点

- Vue 进行数据拦截/代理，对侦测数据的变化敏感精确，动了多少数据就触发多少更新。
- vue hook 只会被注册调用一次。
- Vue 事件处理函数中的 this 默认指向组件实例。
- React 推崇函数式，进行局部重新刷新渲染，递归 React.createElement 的执行调用。对数据变化无感知，触发局部变化由开发者手动调用 setState 完成。
- 每次组件被 render 的时候都会顺序执行所有的 hooks。
- React 事件系统庞大复杂，暴漏给开发者的事件不是原生事件，是 React 包装过合成事件。
- React 中事件处理函数中的 this 默认不指向组件实例。

### vue全家桶

  vue-router：

  定义：import Router、注册插件Vue.use(VueRouter)，配置pageRouter、实例化new Router(pageRouter)、注入Vue实例

  嵌套路由：```<router-view></router-view>```标签嵌套 + children

  路由跳转：

  1. 导航链接 ```<router-link to="/foo">去</router-link>```
  2. router.push(name:'A',path:'/a',query:{id:1})

  传参：

   1. 使用path来匹配路由，然后通过query来传递参数，通过this.$route.query取参数；
   2. 使用name来匹配路由，然后通过params来传递参数，通过this.$route.params取参数；
   3. 使用a/1102032037来匹配路由，路由配置:{path:'/a/:id'}，通过this.$route.params取参数。

  懒加载：上

  动态路由匹配：使用动态路径参数把某种模式匹配到的所有路由全都映射到同个组件
  路由配置：{path:'/demo/:id, name:'demoPage', component:...'}
  访问路径：localhost:8080/#/demo/666
  参数获取：this.$route.params -> {id: 666}

  导航守卫、钩子函数：

  1. 导航被触发。
  2. 在失活的组件里调用组件内钩子 beforeRouteLeave
  3. 调用全局的钩子 beforeEach，主要是用于登录验证，在路由还没跳转提前告知
  4. 紧随执行 beforeEnter，在各自路由配置处。
  5. 解析异步路由组件。
  6. 在被激活的组件里调用组件内钩子 beforeRouteEnter。
  7. 调用全局解析守卫 beforeResolve
  8. 导航被确认
  9. 在路由跳转完成后调用全局钩子 afterEach
  10. 进入组件生命周期beforeCreate-->created-->beforeMount-->mounted，触发 DOM 更新。
  11. 在导航被确认后执行 beforeRouteEnter 守卫中 next 回调函数，把组件实例作为回调方法的参数。
  12. 在重用的组件里调用 beforeRouteUpdate

  spa路由原理：
  2种实现方式：

  1. window.history
     - HTML5的History接口允许我们操作浏览器会话历史记录。
     - history.pushState向历史栈中写入数据，history.replaceState替换修改浏览历史中当前纪录。每当一个文档倒退或前进浏览历史出现变化时会触发popstate事件。
     - 这样就可以在监听事件的回调函数中，执行我们展示和隐藏不同UI显示的功能，从而实现前端路由。
  2. location.hash
     - 在url中以#结尾的hash值，改变页面的hash值使页面完整的url发生了改变，但是页面是不会刷新。
     - hash值改变时，会触发hashchange的事件，得到一个HashChangeEvent。
     - 有了监听事件就可以执行展示和隐藏不同UI显示的功能，从而实现前端路由。

vuex：vuejs管理数据状态，通过创建一个集中的数据存储，供程序当中所有的组件访问。

- 在组件中使用辅助函数mapState：mapState函数返回一个对象，可将state数据映射到局部属性中/this.$store.state。
- 可在组件computed中获取到store然后可进行相应计算处理，渲染至页面。
- 可将计算store的方法抽离一个共享函数：getter方法，相当与store的计算属性，返回新的值。
- 然后在组件computed中可通过this.$store.getters.调用获取store状态值。
- 在组件中使用辅助函数mapGetters：可将 store 中的 getter 映射到局部计算属性。
- 触发改变store：在组件的方法中this.$store.commit相应的mutation改变store中的状态。
- 每个 mutation 都有一个字符串的事件类型(type)和一个回调函数(handler)。
- 需要以 mutation 相应的 type 调用 store.commit 方法。
- 以常理定义type，存放至单独文件可以使得mutation一目了然。
- 以type常量作为mutations函数名。必须是同步函数，任何在回调函数中进行的状态的改变都是不可追踪的。
- 在组件中使用辅助函数mapMutations，可将组件中的 methods 映射为 store.commit 调用。
- 为了实现可在异步回调中改变状态，使用action。
- Action函数包含异步操作，但不直接变更状态，而是异步回调后提交相应的mutation。
- Action函数接受一个与 store 实例具有相同方法和属性的 context 对象，通过context.commit 提交一个 mutation。
- Action 通过 store.dispatch 方法触发.
- 在组件中使用辅助函数mapActions：将组件的 methods 映射为 store.dispatch 调用.

  ​axios：不是vue里的，代替vue-resource

### vue3

- 提升运行时性能，重写VDOM，跳过静态节点，只处理动态节点，速度更快；
- 提升网络性能，引入treeshaking机制，只打包必要的依赖项，项目最后打包的体积最小化；
- 所有组件均可按需加载，更灵活的组件化；
- 完全的typescript支持；
- composition-api:
  - setup 初始化函数返回一个对象暴露给模板，即为声明的数据，
  - 在 setup 中 this 为 undefined
  - setup 函数俩参数：props 获取父组件传来的参数；context 向外发布事件和数据 context.emit
  - 用 ref 或者 reactive 包裹的数据为响应式的，为此开发者可以自行定义那些数据是需要响应式的，哪些数据不需要
  - 更易维护：在同一个方法中完成同一个需求的所有功能
- vite: 快！快速冷启动，即时模块热更新，按需编译
  - script module 是 ES 模块在浏览器端的实现，使用 export、import 的方式导入和导出模块，浏览器将对其内部的 import 引用发起 http 请求获取模块内容，ESM 天生按需加载，只有 import 的时候才会去按需加载。
  - webpack 使用 map 存放模块 id 和路径，使用 webpack_require 方法获取模块导出，不管某个模块的代码是否执行到，这个模块都要打包到 bundle 里，随着项目越来越大打包后的 bundle 也越来越大。

  对Vue.js进行了完全Typescript重构，让Vue.js源码易于阅读、开发和维护；
重写了虚拟Dom的实现，对编译模板进行优化、组件初始化更高效， 性能上有较大的提升；Vue.js2对象式组件存在一些问题：难以复用逻辑代码、难以拆分超大型组件、代码无法被压缩和优化、数据类型难以推倒等问题；而CompositionAPI 则是基于函数理念，去解决上述问题，使用函数可以将统一逻辑的组件代码收拢一起达到复用，也更有利于构建时的tree-shaking检测，这个使用起来有些类似于React的hook；

### AngularJS项目

- 特性：
  - 单页面
  - 模板机制
  - 双向数据绑定-摆脱繁琐的DOM操作
  - MVC：解耦应用逻辑C、数据模型M和视图V；controller(初始状态和参数化$scope方法)
  - 服务和依赖注入
  - 指令
  - 路由机制
  - <https://www.csdn.net/gather_2e/NtjaggzsODY0LWJsb2cO0O0O.html>
- AngularJS页面中通过挂在方法到window上，供GIS调用，并传递地理位置给2屏模块，以此获取参数重载数据，
- 利用iframe将第三方应用的网页嵌入到自己web工程中
  - 数据通信兼容跨域：
    - 父向子->父：frame.contentWindow.postMessage ("数据", '*')，子：window. addEventListener ('message', function(event) {});
    - 子向父->子：window.parent.postMessage(data,'http://l父亲地址/')，父：window. addEventListener ('message', function(event) {});
  - 内容安全策略：管理网站允许加载制定资源。三方应用通过服务器发header头X-Frame-Options的信息控制只允许相同域名下的网页iframe自己。

### SPA

 SPA 不会因为用户的操作而进行页面的重新加载或跳转，利用路由机制实现 HTML 内容的变换。
 用户体验好，相对对服务器压力小。
 项目架构清晰。
 内容都在一个页面中动态替换显示使得在SEO上有弱势。

### 前端页面构成

- 结构层:搭建文档的结构。html
- 表示层:设置文档的呈现效果。css
- 行为层:使用 DOM 脚本去实现文档的行为。js

### 前端工程化、自动化

 前端工程化：一系列提升前端开发效率，提高前端应用质量的手段和工具。

从项目组织上包括：

 1. 开发速度
 2. 部署速度
 3. 重构速度
 4. 可测试性
 5. 可变性
 6. Bug的重现与定位等

从技术架构上包括：

 1. 模块化：功能的模块化划分，文件层面；
 2. 组件化：界面的组件化，UI层面；
 3. 规范化: 统一的开发规范与风格
     - 目录结构的制定
     - 编码规范
     - 前后端接口规范
     - 文档规范
     - 组件管理
     - Git分支管理
     - Commit描述规范
     - 定期codeReview
     - 视觉图标规范
 4. 自动化:
     - 自动化构建：
     - 自动化部署：
     - 自动化测试：
     - 持续集成CI：

 Jenkins：开源持续集成工具，具有自动化构建、测试和部署等功能。
 其他：Travis、Gitlab-CI、docker、k8s

 前端项目构建是通过前端自动化构建工具自动化地执行一系列复杂地流程，自动代码编译/文件优化/代码分割/代码压缩/自动刷新/代码校验/版本生成
 只要工具有基于模块化：Browserify、Webpack、rollup.js；基于任务：Gruntn Grunt；整合型：百度FIS,腾讯Modjs，360燕尾服，Yeoman、jdf

 前端自动化测试大致包括：类库单元测试（让不同浏览器自动根据指令跑一些JS函数结果与预期比对后返回是否通过case测试标志）和UI组件测试（使用Selenium、phantomjs 模拟操作实现）

 持续集成是指代码集成到主干之前，必须通过自动化测试。只要有一个测试用例失败，就不能集成。目的就是让产品可以快速迭代，同时还能保持高质量。
 合并到 develop 分支触发 CI 成功后快速发布部署到测试或预发布环境通过测试人员的测试和一定的自动化测试。到需要发布的时间点，再拉取 master 分支来构建部署发布。

 webhooks可以通过监听push触发回调，发送post请求到所指定的地址，服务端收到该请求进行对应的git pull更新代码的操作。

 前端架构图

### 多端开发

 写一次代码，就可以编译出在不同端（微信 / 百度 / 支付宝小程序、H5、React-Native 等）都能运行的代码。

  Vue.js 开发跨平台应用的前端框架：uni-app
  京东开源的一套遵循 React 语法规范的多端开发解决方案：Taro

### 工作流

分类：

 1. Git flow：适于版本发布
    - 两个长期分支：
       - 主分支master
       - 开发分支develop；
    - 三种短期分支：
       - 功能分支（feature branch）
       - 补丁分支（hotfix branch）
       - 预发分支（release branch）
 2. Github flow：适于持续发布，支持快速迭代，快速部署，用于变化多端的前端项目
    - 一个长期master分支和多个短期分支
    - 不区分功能分支或补丁分支，根据需求直接从master拉出新分支
 3. Gitlab flow：综合两者：
    - 持续发布："开发环境"的分支是master，"预发环境"的分支是pre-production，"生产环境"的分支是production。
    - 版本发布：每一个稳定版本，都要从master分支拉出一个分支，以后，只有修补bug，才允许将代码合并到这些分支，并且此时要更新小版本号。

 （参考：<https://zhuanlan.zhihu.com/p/101080514>）

### PWA

PWA：Progressive Web App，渐进式WEB应用。

- 使用一系列现代Web API新技术和传统的渐进式增强的策略创建应用程序；
- 旨在为网页提供App原生应用般的使用体验；
- vue、react脚手架已经集成PWA；
- 渐进式：浏览器若不兼容这些API，则向下兼容；
- 流畅：借助serviceWorker，在离线情况下也可正常访问，传统网页断网了，刷新页面就加载不出来了；
- 可安装：用户可通过网址添加常用webapp到桌面，体验和原生应用差不多，有首屏加载动画，隐去地址栏等；
- 粘性：可以离线推送通知；
- 仅支持hppts协议域名和 localhost 下访问。

核心技术：

1. Web App Manifest 应用程序清单
   - 解释：一个JSON文件，提供了有关应用程序的信息；
   - 作用：实现添加到桌面，有图标和名称，有启动界面，隐藏地址栏等浏览器相关UI；
   - 使用：创建manifest.json文件,在index.html中引入，```<link rel="manifest" href="manifest.json"/>```；
   - 文件内容配置
2. Service Worker
   - H5 API，主要用来做持久离线缓存，浏览器navigator的内置属性；
   - 独立的线程，一种特殊的Web Worker，
   - 相当于代理服务器，可以拦截请求，可以操作缓存，可以发送请求；
   - 离线的内容开发者自省掌控；
   - 使用：
     - 在window.onload中注册serviceWorker，防止初始加载资源竞争；
     - 能力监测：老版本不兼容，条件判断有此属性再注册;
     - 注册：navigator.serviceWorker.register("sw.js).then(()=>{}).catch(()=>{})；
     - serviceWorker生命周期事件：install、activate、fetch；
     - 获取静态资源，请求发送触发fetch事件，在此设置走网络还是取缓存，走网络用fetch api，取缓存用cache storage。
3. fetch api
   - 网络请求和响应的api，与ajax相比可以被使用到更多的应用场景；
   - Service Worker中无法使用XMLHttpRequest，必须使用fetch api；
   - 基于promise实现；
   - window.fetch；
   - 请求得到的是二进制流；
4. cache storage
   - window.cache对象的存储，配合Service Worker使用；
   - 一系列方法把请求和对应的结果存储起来；
5. Notifications API
   - window.Notifications;
   - 通知接口用于向用户配置和显示桌面通知，告诉用户现在有网没网，看到的数据是缓存还是网络请求；

### 前端技术选型

分析业务类型和应用系统：

 1. 页面重展示、轻交互:
    - 要求：稳定、快速、无障碍、可靠、兼容、利于SEO；
    - 技术选型：可服务端渲染SSR。
 2. 页面轻展示、重交互：
    - 要求：完成复杂交互，代码简单，容易维护；
    - 技术选型：适当引入mvvm库，极大减少代码量，提高性能。
 3. 运营后台系统：
    - 特点：多表单操作、查询条件因素丰富、列表数据展示、图形报表展示、增删改查等业务操作；
    - 要求：统一的UI、交互规则，代码复用率高，交互复杂；
    - 技术选型：SPA + UI库，根据团队情况选择适合的框架和库。
 4. 需要持续迭代的长期项目：
    - 项目代码可维护性，业务隔离，代码足够小，适应移动端复杂的网络环境；
    - 从渲染性能、文件大小等方面考虑。
 5. SPA框架选择：
    - vue：web开发，单页面应用程序；
    - React：IOS、Android、web开发、原生渲染应用程序、单页面应用；
    - 大规模功能丰富的应用程序，native应用、混合应用、web应用

此外：

- 开发效率优先还是运行效率优先；
- 成熟和常见技术优先；
- 正确评估下团队开发的接受能力；
- 遇到问题时尽可能使用现有的解决方案来解决技术问题；
- 在选择技术时，优先考虑社区规模和维护活跃度，尤其是在不熟悉的领域；
- 在考虑新技术时要谨慎，偏向保守的选择。

 SSR：
 在客户端将标签渲染成整个 html 片段的工作在服务端完成，服务端返回已经渲染好的页面给客户端。
 数据已经包含在页面中，首屏加载更快，搜索引擎爬取工具可以抓取渲染好的页面；

### 前端开发规范

 1. JavaScript编码规范
 2. HTML编码规范
 3. CSS编码规范
 4. 项目目录结构规范
 5. 编辑器配置和构建检查

- 缩进
- 空格
- 换行
- 语句：如：不得省略块 {...}、函数定义结束不允许添加分号
- 命名：js：Camel命名法/Pascal命名法--名词、动宾短语。css：class->小写+-，属性->纯小写，以内容和功能命名。
- 注释
- 语言特性：如：变量或函数在使用前必须先定义、每个var只能声明一个变量、变量必须即用即声明不得预先统一声明、条件判断使用全等
- 目录命名简洁且有习惯性缩写的单词，不允许使用复数形式
- 根据业务逻辑划分src目录结构
 （参照:<https://github.com/ecomfe/spec>）

### 技术攻坚

- el-table组件通过其暴露的render-header方法，使用vue的渲染函数createElement在表头内部嵌入tip指标说明提示：

  ```javascript
        //createElement(标签名，attr数据对象，子级虚拟节点['文本节点'，createElement创建子级节点])
        createElement(
              "span",
              [
                '莹',
                createElement(
                  "el-tooltip",
                  {
                    class: "cell-s-tip tableColumnsDoubt",
                    props: {
                      effect: "dark",
                      placement: "bottom",
                      popperClass: "tableColumnsTip"
                    }
                  },
                  [
                    createElement(
                      "i",
                      {
                        class: "fa fa-question-circle"
                      }),
                    createElement(
                      'div',
                      {
                        slot: 'content',
                        domProps: {
                          innerHTML: '莹：是我的名字'
                        }
                      }
                    )
                  ]
                )
              ]);

  ```

- Echarts三级下钻渲染，遇到问题时尽可能使用现有的解决方案来解决技术问题；
- 横向表格树，可复选框勾选：渲染函数render方法createElement，递归创建元素。
- 传递参数过大导致导出文件失败，get方法导出->改为使用表单导出文件：
  - 创建form元素
  - form.style.display = 'none';
  - form.action = url;
  - form.method = "post";
  - form.acceptCharset = "UTF-8";
  - form.enctype = "multipart/form-data";
  - form.target = "_blank";
  - appendChild(form);
  - 遍历params循环创建input并挂入form
  - input.type = "hidden";
  - input.name = key;
  - input.value = params[key];
  - form.appendChild(input);
- 刷新页面保留当前路由，点击当前路由菜单刷新当前页面。
- RaphaelJS横向漏斗图-转化漏斗：
  - 借助Raphael方法，创建一个画布，生成一块SVG区域
  - 使用x,y坐标系去绘制图形
  - ,rect()方法创建矩形。4个必须：x坐标、y坐标、矩形宽度、矩形高度
  - .path(`M50, 0L10, 50L100, 200L50, 200Z`);
  - .attr('fill', '#46a4d1');
  - .attr('stroke', '#e9f4f9');
- AntV G6、Draggable 实现拖拽编辑流程图
- 计算规则编辑的交互实现

### typescript

 1. js项目如何升级为ts？有何影响？
     ts完全兼容js代码，无需修改可平滑迁移。是编译型语言，需要编译成js后才能被浏览器执行。

 2. ts 基础类型都哪些，他们跟js的区别？
     - string、boolean、number 与js相同；
     - 数组：
        - 元素类型后面接上[]： let list: number[] = [1, 2, 3];
        - Array<元素类型>：let list: Array< number > = [1, 2, 3];
        - 表示一个已知元素数量和类型的数组，各元素的类型不必相同：let x: [string, number] = [‘q’, 2];
     - 枚举enum：为一组数值赋名，对js标准数据类型的补充；
     - any：表示任意JavaScript值；
     - void：所有类型都不存在的时候。
     - undefined和null->undefined和null,是所有类型的子类型.

 3. ts为什么会流行？与ECMA新规范的关系？
    - ts有强大的类型系统，具备静态类型检查能力，开发环境能提供丰富的信息，大部分检查语言本身完成，提高代码的健壮性。
    - 增强的class，具备成员访问控制，静态成员和自读成员等。
    - 增强的面向对象编程思想，接口：用函数签名定义行为的抽象类型，一个接口实例必须遵循接口规则。泛型：创建可重用的组件，一个组件支持多种类型的数据。
    - js是ECMA标准的一个实现，ts是js的一个超级，需要编译成js后方能运行，ts支持ECMA新标准。

 4. tslint都能配置哪些功能？对开发流程有何影响？
    - TS特性："no-empty-interface":true,// 不允许空接口   no-any: true,//不许使用any类型
    - 功能特性： "await-promise":true,// 不允许没有Promise的情况下使用await "no-for-in-array":true,// 不允许对Array使用for-in
    - 维护性功能："indent":[true, "spaces", 4],// 每行开始以4个空格符开始 "max-line-length":[true,120],// 定义每行代码数
    - 格式："class-name":true,// 类名以大驼峰格式命名 "import-spacing":true,// import关键字后加空格

### 兼容问题有哪些

- 安卓元素无法垂直居中问题偏上一些，不能垂直居中，解决  display: flex;align-items: center; justify-content: center；
- ios滚动卡顿  -webkit-overflow-scrolling: touch
- click 300ms 延时响应  FastClick
- 安卓部分版本input里的placeholder位置偏上 把input的line-height设为normal
- 输入框在固定在最上面，但是用ios下当键盘弹起时fixed会失效。把页面滚动改为容器内滚动。
- ios滚动时动画停止  better-scroll想·
- 禁止数字识别为电话号码  ```<meta name = "format-detection" content = "telephone=no">```
- 滚动穿透问题  借助滚动条插件  弹层中 弹层出现的时候给body增加overflow:hidden 弹层关闭时去掉

### JSbridge

### nodejs

- 前端js：js（遵循es语法规范） + web API（遵循w3c标准-dom操作、bom操作、事件绑定、ajax等）
- nodejs：js（遵循es语法规范） + nodejs API（http、fs等）
- nodejs 中默认的模块化规范 commonjs
- 接口开发：处理 http 请求，开发接口，get 请求与 querystring，post 请求与 postdata，路由，nodemon 开发环境修改后自动重启
- stream 写日志，Redis 存 session
- pm2 进程守候

### MySQL

- 设置当前使用某个库 ```use myblog;```
- 查看当前库所有表 ```show tables;```
- ```insert into users (username, `password`,  realname) values ('lisi', '123', '李四'  );```，向 user 表中插入数据，password 为关键字，使用反引号括起来即可
- 查询所有表数据 ```select * from users;```
- 查询表某些列数据 ```select id, username from users;```
- 按条件查询表数据 ```select * from users where username = 'zhangsan' and `password` = '123';```
- 模糊查询表数据 ``` select * from users where username like '%lisi%' ```
- 查询数据排序 ```select id, username from users order by id;```，```select id, username from users order by id desc;```
- 更新表数据 ```update users set realname = '李四2' where username = 'lisi';```
- 删除表数据 ```delete from users where id = 4;```
- 软删除 ```update users set state = '0' where username = 'lisi';```，```select * from users where state <> '0';```
- 补充-修改表 column 名字 ```alter table blogs change column creattime createtime varchar(45);`，其中可修改内容： blogs 为表的名字，creattime 为 旧 column 名，createtime 为新 column 名，varchar(45)为新 column 类型