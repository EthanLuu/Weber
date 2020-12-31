## 样式表和选择器

Cascading Style Sheet，层叠样式表，用于给 HTML 页面标签添加各种样式，定义网页的显示效果

CSS 将网页内容和显示样式进行分离，增强了显示功能。

**HTML 的缺陷**

1. 不能够适应多种设备
2. 要求浏览器必须智能化足够庞大
3. 数据和显示没有分开
4. 功能不够强大

**CSS 优点**

1. 使数据和显示分开
2. 降低网络流量
3. 使整个网站视觉效果一致
4. 使开发效率提高了

### CSS 语法

```css
选择器 {
    k: v;
    k: v;
    k: v;
    k: v;
}
选择器 {
    k: v;
    k: v;
    k: v;
    k: v;
}
```

### CSS 和 HTML 结合的方式

1. 行内样式：某个特定标签内使用 style 属性

2. 内嵌样式表：在页面的 head 里采用 style 标签

3. 引入外部 css 文件的方式

   - 采用 link 标签
   - 采用 import

   > 两种引入方式的区别：外部样式表中不能写 link 标签，但是可以写 import 语句

### CSS 选择器

指定 CSS 作用的标签

选择器总共两大类：基本选择器和扩展选择器

常用的三种器的区别

- 标签选择器针对的是页面上的一类标签
- ID 选择器针对特定的一个标签
- 类选择器可以被多种标签使用

#### 基本选择器

**标签选择器**

选择所有某种类型的标签，用于描述**共性**

- 所有的标签，都可以是选择器
- 选择的是所有，而不是一个

```css
p{ font-size:14px; }
```

p 标签内的文字都是 14px

**ID 选择器**

针对某一个特定的标签来使用，以`#`来定义

```css
#mytitle{ border:3px dashed green;}
```

任何的 HTML 标签都可以有 id 属性。表示这个标签的名字。

这个标签的名字，可以任取，但是：

-   只能有字母、数字、下划线
-   必须以字母开头
-   不能和标签同名
-   HTML 页面不能出现相同的 ID

> 一个标签可以被多个 css 选择器选择，共同作用

#### 类选择器

用`.`来定义某一个类的标签

```css
.eat{
    font-size: 18px;
    font-weight: 900;
}
```

- 不要试图用一个类写完所有标签的样式，多写几个类
- 每一个类尽可能小，有公共的概念，让更多的标签使用
- 到底用 id 还是 class？
  - 尽可能用 class
  - 因为 id 是给 js 使用的，js 通过 id 来获取标签，所以 css 层面尽可能不用 id
  - 另一方面，我们认为一个有 id 的元素，有动态效果
- 类上样式，id 上行为

#### 通用选择器

`*`，匹配任何标签，效率低，不使用

### CSS 的高级选择器

#### 后代选择器

如果选择的是`E F`，表示所有属于 E 元素的后代的 F 元素

```css
div p{
    font-size: 19px;
}

div span{
    font-family: 微软雅黑;
    font-size: 3em
}

<div> <p> wtf </p> </div>
<div> <span> omg </span> </div>
```

#### 交集选择器

两个选择器紧密相连，以标签名开头

如果后一个是类选择器，就写成`div.food`，如果后一个是 id 选择器，就写成`div#food`

```css
div.food{
    font-family: 微软雅黑;
    font-size: 3em;
}
```

#### 并集选择器

简单来说就是多选

```css
p,
h1,
#mytitle,
.one {
    color: red;
}
```

### CSS3 的一些选择器

#### 子代选择器

`>`，只有是儿子的时候才能被选择

```css
div > p {
    color: red;
}
```

只能选择

```html
<div>
    <p>我是div的儿子</p>
</div>
```

不能选择

```html
<div>
    <ul>
        <p>我是div的孙子</p>
    </ul>
</div>
```

#### 序选择器

设置无序列表`<ul>`中的第一个`<li>`为红色：

```css
ul li:first-child {
    color: red;
}
```

设置无序列表`<ul>`中的最后一个`<li>`为红色：

```css
ul li:last-child {
    color: blue;
}
```

#### 下一个兄弟选择器

`+` 表示选择下一个兄弟

把 h3 元素后面的一个 p 标签变成红色

```css
h3 + p{
    color: red;
}
```

## 单位

HTML 的单位只有一种，即像素`px`，所以单位可省略

CSS中必须要写单位，因为没有默认单位

### 绝对单位

- `in`：英寸Inches (1 英寸 = 2.54 厘米)
- `cm`：厘米Centimeters
- `mm`：毫米Millimeters
- `pt`：点Points，或者叫英镑 (1点 = 1/72英寸)
- `pc`：皮卡Picas (1 皮卡 = 12 点)

换算规则

`1 in` = `2.54 cm` = `25.4 mm` = `72 pt` = `6 pc`

### 相对单位

`px`：像素
`em`：印刷单位相当于12个点
`%`：百分比，相对周围的文字的大小

## 字体属性

常见字体属性

```css
p{
	font-size: 50px; 		/*字体大小*/
	line-height: 30px;      /*行高*/
	font-family: 幼圆,黑体; 	/*字体类型：如果没有幼圆就显示黑体，没有黑体就显示默认*/
	font-style: italic ;		/*italic表示斜体，normal表示不倾斜*/
	font-weight: bold;	/*粗体*/
	font-variant: small-caps;  /*小写变大写*/
}
```

为了严格保证字在行里面居中，我们的工程师有一个约定： **行高、字号，一般都是偶数**。这样可以保证，它们的差一定偶数，就能够被2整除。

### 如何让单行文本居中

如果文本只有一行，那么将**行高**和**盒子高**设置成一样大，就可以保证单行文本垂直居中。

如果需要多行文本居中就需要根据总行高自己算 top-margin

也可以使用`vertical-algin`属性来使指定**行内元素**（inline）、**行内块元素**（inline-block）、**表格的单元格**（table-cell）的垂直对齐方式。主要是用于图片、表格、文本的对齐。

```css
vertical-align: middle; /*指定行级元素的垂直对齐方式。*/
```

### 字号 行高 字体

```css
font-size: 14px;
line-height: 24px;
font-family: "宋体";
/* 将字体属性连写 (字体粗细 字号/行高 字体) */
font: 400 14px/24px "宋体";
```

一般将英文字体放在最前面，这样做到中英文字体分离

```css
font-family: "Times New Roman","微软雅黑","宋体";
```

## 文本属性

- `letter-spacing: 0.5cm ;`  单个字母之间的间距
- `word-spacing: 1cm;`   单词之间的间距
- `text-decoration: none;` 字体修饰：none 去掉下划线、**underline 下划线**、line-through 中划线、overline 上划线
- `text-transform: lowercase;`  单词字体大小写。uppercase大写、lowercase小写
- `color:red;` 字体颜色
- `text-align: center;` 在当前容器中的对齐方式。属性值可以是：left、right、center（**居中**）、justify
- `text-transform: lowercase;` 单词的字体大小写。属性值可以是：`uppercase`（单词大写）、`lowercase`（单词小写）、`capitalize`（每个单词的首字母大写）

### 列表属性

```css
ul li{
	list-style-image:url(images/2.gif) ;  /*列表项前设置为图片*/
	margin-left:80px;  /*公有属性*/
}
```

### overflow 属性

用来处理超出范围的内容

`overflow`属性的属性值可以是：

- `visible`：默认值。多余的内容不剪切也不添加滚动条，会全部显示出来。
- `hidden`：不显示超过对象尺寸的内容。
- `auto`：如果内容不超出，则不显示滚动条；如果内容超出，则显示滚动条。
 - `scroll`：Windows 平台下，无论内容是否超出，总是显示滚动条。Mac 平台下，和 `auto` 属性相同。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>EthanLoo's</title>
    <style type="text/css">
      div {
        width: 100px;
        height: 100px;
        margin-right: 100px;
        float: left;
      }

      #div1 {
        overflow: auto; /*超出的部分浏览器解决*/ 
      }

      #div2 {
        overflow: visible; /*超出的部分显示*/ 
      }
      
      #div3 {
        overflow: hidden; /*超出的部分隐藏*/ 
      }
    </style>
  </head>
  <body>
    <div id='div1'>
      什么是前端工程师？总而言之前端工程师就是运用HTML/CSS/JavaScript等Web技术，在工作中配合设计师实现用户界面，和后端工程师进行数据对接，完成Web应用开发的职位。
    </div>
    <div id='div2'>
      什么是前端工程师？总而言之前端工程师就是运用HTML/CSS/JavaScript等Web技术，在工作中配合设计师实现用户界面，和后端工程师进行数据对接，完成Web应用开发的职位。
    </div>
    <div id='div3'>
      什么是前端工程师？总而言之前端工程师就是运用HTML/CSS/JavaScript等Web技术，在工作中配合设计师实现用户界面，和后端工程师进行数据对接，完成Web应用开发的职位。
    </div>
  </body>
</html>
```

## 背景属性

### background-color 背景颜色

css2.1 中的三种表示方法

1. 单词
2. RGB 表示法
3. 16进制表示法

```css
background-color: red;
background-color: rgb(255,0,0);
background-color: #ff0000;
```

css3 中新增的颜色表示方法

1. RGBA 表示法
   - 红 绿 蓝 透明度
2. HSLA 表示法
   - 色调 饱和度 亮度 透明度

```css
background-color: rgba(0, 0, 255, 0.3);
background-color: hsla(240,50%,50%,0.4);
```

### background-repeat

- `repeat` 默认值，平铺满

- `no-repeat`（不要平铺）
- `repeat-x`（横向平铺）
- `repeat-y`（纵向平铺）

### background-position

- 背景定位

1. 用像素描述

   ```css
   background-position:向右偏移量 向下偏移量;
   ```

2. 用单词描述

   ```css
   background-position: 描述左右的词 描述上下的词;
   ```

### background-attachment

- 控制背景是否固定
  - fixed 固定
  - scroll 不固定

```css
background-attachment:fixed;
```

### background 综合属性

```css
background:red url(1.jpg) no-repeat 100px 100px fixed;
```

等价于

```css
background-color:red;
background-image:url(1.jpg);
background-repeat:no-repeat;
background-position:100px 100px;
background-attachment:fixed;
```

### background-size

```css
/* 宽、高的具体数值 */
background-size: 500px 500px;

/* 宽高的百分比（相对于容器的大小） */
background-size: 50% 50%;   // 如果两个属性值相同，可以简写成：background-size: 50%;

background-size: 100% auto;  //这个属性可以自己试验一下。

/* cover：图片始终填充满容器，且保证长宽比不变。图片如果有超出部分，则超出部分会被隐藏。 */
background-size: cover;

/* contain：将图片完整地显示在容器中，且保证长宽比不变。可能会导致容器的部分区域为空白。  */
background-size: contain;
```

### background-origin

控制从什么位置开始显示背景

```css

/* 从 padding-box 内边距开始显示背景图 */
background-origin: padding-box;           //默认值

/* 从 border-box 边框开始显示背景图  */
background-origin: border-box;

/* 从 content-box 内容区域开始显示背景图  */
background-origin: content-box;

```

### background-clip

设置元素的背景是否延伸到边框下面

 - `border-box` 超出 border-box 的部分，将裁剪掉

 - `padding-box` 超出 padding-box 的部分，将裁剪掉

 - `content-box` 超出 content-box 的部分，将裁剪掉

### background-image

1. 线性渐变：沿着某条直线朝一个方向产生渐变效果。
2. 径向渐变：从一个**中心点**开始沿着**四周**产生渐变效果。
3. 重复渐变

![](https://cdn.ethanloo.top/img/20201224225320.png)

#### 线性渐变

```css
background-image: linear-gradient(方向, 起始颜色, 终止颜色);

background-image: linear-gradient(to right, yellow, green);
```

#### 径向渐变

```css
background-image: radial-gradient(辐射的半径大小, 中心的位置, 起始颜色, 终止颜色);

background-image: radial-gradient(100px at center,yellow ,green);
```

### Clip-path

`clip-path`属性可以创建一个只有元素的部分区域可以显示的剪切区域。区域内的部分显示，区域外的隐藏。

鼠标悬停放大图片

```css
.div1 {
    width: 320px;
    height: 320px;
    border: 1px solid red;
    background: url(http://img.smyhvae.com/20191006_1410.png) no-repeat;
    background-size: cover;

    /* 裁剪出圆形区域 */
    clip-path: circle(50px at 100px 100px);
    transition: clip-path .4s;
}
.div1:hover{
    /* 鼠标悬停时，裁剪出更大的圆形 */
    clip-path: circle(80px at 100px 100px);
}
```

## 伪类选择器

伪类是用来添加一些选择器的特殊效果。

比如 div 是属于 box 类的，这很明确，但是 a 属于什么类是不明确的，需要看用户点击前的状态和点击后的状态。

### 静态伪类和动态伪类

#### 静态伪类

只能用于超链接的样式

- `:link` 超链接点击之前
- `:visited` 链接被访问过之后

#### 动态伪类

针对所有标签都适用的样式

- `:hover` “悬停”：鼠标放到标签上的时候
- `:active`	“激活”： 鼠标点击标签，但是不松手时。
- `:focus` 是某个标签获得焦点时的样式（比如某个输入框获得焦点）

### a 标签

超链接的四种状态

- `:link`  	“链接”：超链接点击之前
- `:visited` “访问过的”：链接被访问过之后
- `:hover`	“悬停”：鼠标放到标签上的时候
- `:active`	“激活”： 鼠标点击标签，但是不松手时。

在 CSS 中，这四种状态必须按照固定的顺序写

```css
a:link {
  color: antiquewhite;
}

a:visited {
  color: green;
}

a:hover {
  color: salmon;
}

a:active {
  color: skyblue;
}

```

制作一个导航

```html
  <body>
      <nav>
        <li><a href="">百度</a></li>
        <li><a href="">谷歌</a></li>
        <li><a href="">雅虎</a></li>
        <li><a href="">bilibili</a></li>
      </nav>
  </body>
```

```css
nav {
  width: 400px;
  height: 50px;
  margin: 100px auto;
  border: 1px solid black;
  background-image: linear-gradient(to right, #C9D6FF, #E2E2E2);
}

nav li {
  list-style: none;
  float: left;
  width: 100px;
  height: 50px;
  text-align: center;
  line-height: 50px;
}

nav li a {
  display: block;
  width: 100px;
  height: 50px;
  
}

nav a:link,
nav a:visited {
  text-decoration: none;
  
  color: black;
}

nav li a:hover {
  background-image: linear-gradient(to right, #acb6e5, #acb6e5);
}
```

![image-20201226154801929](https://cdn.ethanloo.top/img/20201226154801.png)

标准写法是 link，visited 和 hover 这三个伪类都需要写。

一般开发的时候 `a:link, a:visited` 都可以省略，简写在 `a` 标签里。

### 动态伪类

- `:hover` 悬停
- `:active` 激活
- `:focus` 获得焦点

```html
  <body>
    <input type="text" name="" id="test-input" />
    <br />
    <div>
      麻烦点我一下
    </div>
  </body>
```

```css
div:hover {
  color: green;
}
div:active {
  color: purple;
}
div:focus {
  color: red;
}
input:hover {
  color: green;
}
input:active {
  color: purple;
}
input:focus {
  color: red;
}
```

## CSS 继承性和层叠性

### CSS 的继承性

- 关于文字样式的属性，都具有继承性。
  - 这些属性包括：color、 text-开头的、line-开头的、font-开头的。
- 关于盒子、定位、布局的属性，都不能继承。

### CSS 的层叠性

当多个选择器，选择了某个元素的时候，要按照如下顺序统计权重：

-  id 选择器
-  类选择器、属性选择器、伪类选择器
-  标签选择器、伪元素选择器

1. 计算权重

   统计各个选择器的数量，优先级高的胜出，图中的 p 标签是红色

   ![img](http://img.smyhvae.com/20170725_2138.png)

2. 权重相同时

   就近原则，以后一个样式为准

3. 尝试实现

   ![image-20201226161151085](https://cdn.ethanloo.top/img/20201226161151.png)

   ```html
     <body>
       <div class="sr">
         <ul>
           <li class="ssr">word</li>
           <li>word</li>
           <li>word</li>
           <li>word</li>
           <li>word</li>
           <li>word</li>
           <li>word</li>
         </ul>
       </div>
     </body>
   ```

   错误写法

   ```css
   .sr ul li{
       color: blue;
   }
   
   .ssr{
       color: red;
   }
   ```

   > 这样写的话第一个的选择器的权重为 0 1 2，第二个选择器的权重为 0 1 0

   正确写法

   ```css
   .sr ul li{
       color: blue;
   }
   
   .sr ul li.ssr{
       color: red;
   }
   ```

4. 继承性的说明

   如果不能直接选中某个元素，通过继承性影响的计算的权重为0，最后显示的颜色为 blue

   ```html
     <body>
       <div class="sr">
         <div class="ssr">
           <p>666</p>
         </div>
       </div>
     </body>
   ```

   ```css
   p {
     /* 权重0,0,1 */
     color: blue;
   }
   
   .ssr {
     /* 权重0,0,0 */
     color: red;
   }
   
   .sr {
     /* 权重0,0,0 */
     color: green;
   }
   ```

### 层叠性权重计算总结

![](http://img.smyhvae.com/20170727_2050.png)

1. 对于相同权重的选择器，其排序为：行级样式 > 内嵌样式表 > 外部样式表
2. 对于相同类型的样式表，其选择器排序为：ID选择器 > 类选择器 > 标签选择器
3. 外部样式表的 ID 选择器 > 内嵌样式表的标签选择

### !important 标记

```css
font-size:60px !important;
```

1. `!important` 提升的是一个属性，不是选择器
2. `!important` 无法提升继承的权重，该是0还是0
3. `!important` 无法影响就近原则

>  尽量不要用

## 盒模型

包括 div, span, a

**一个盒子的五个主要属性**

- width和height：**内容**的宽度、高度（不是盒子的宽度、高度）
- padding：内边距
- border：边框
- margin：外边距

![](http://img.smyhvae.com/20170727_2326.png)

> 上面这个盒子实际上是 302*202，因为有边框

### padding

padding 就是内边距，padding 实际上也会有背景颜色

有四个方向的 padding

```css
padding-top: 30px;
padding-right: 20px;
padding-bottom: 40px;
padding-left: 100px;
```

综合属性的写法是：上 右 下 左

```css
padding:30px 20px 40px 100px;
```

如果只写三个值，顺序是：上  右 下  // 左和右相等

如果只写了两个值：顺序是：上 右 // 下和上相等，左和右相等

### border

border 本身是一个综合属性

```css
border:1px solid red;
```

两种拆的方式

1. 按三要素拆

   ```css
   border-width:10px;    //边框宽度
   border-style:solid;   //线型
   border-color:red;     //颜色。
   ```

2. 按方向拆

   ```css
   border-top:10px solid red;
   border-right:10px solid red;
   border-bottom:10px solid red;
   border-left:10px solid red;
   ```

3. 当然也可以全部拆开，写成12行

利用 border 画一个🔺

```css
div {
  height: 0px;
  width: 0px;
  border-bottom: 30px solid red;
  border-left: 20px solid transparent;
  border-right: 20px solid transparent;
}
```



![image-20201226193840228](https://cdn.ethanloo.top/img/20201226193840.png)

## 浮动

### 标准文档流

**特性**

1. 空白折叠现象

   无论多少空格，换行，都会折叠成一个空格。

2. 高矮不齐，底边对齐

3. 自动换行，一行写不满，换行写

#### 行内元素和块级元素

标签分为两种等级

- 行内元素
- 块级元素

**两者区别**

- 行内元素
  - 与其他行内元素并排
  - 不能设置宽、高，默认宽度就是文字的宽度
- 块级元素
  - 霸占一行，不能与其他元素并列
  - 能设置宽、高，如果不设置宽度，宽度默认是父类的100%

**两者分类**

HTML 角度

- 文本级标签：p、span、a、b、i、u、em
- 容器级标签：div、h系列、li、dt、dd

CSS 角度

- 行内元素：span、a、b、i、u、em

- 块级元素：**p**、div、h系列、li、dt、dd

> 只有 p 变了个位置

#### 行内和块级的转换

```css
display: inline;
display: block;
```

### 实现浮动

> css 里布局用的最多的属性

div 本身是一个块级元素

```
.ssr{
  height: 200px;
  width: 300px;
  background-color: aquamarine;
}

.sr{
  height: 200px;
  width: 200px;
  background-color: cadetblue;
}
```

<img src="https://cdn.ethanloo.top/img/20201226195415.png" alt="image-20201226195415524" style="zoom: 33%;" />

但是加上浮动之后就可以并排了

```css
.ssr {
  height: 200px;
  width: 300px;
  background-color: aquamarine;
  float: left;
}

.sr {
  height: 200px;
  width: 200px;
  background-color: cadetblue;
  float: left;
}

```

<img src="https://cdn.ethanloo.top/img/20201226195443.png" alt="image-20201226195442936" style="zoom: 33%;" />

- 浮动的元素脱离标准流

  一旦一个元素浮动了，就能够并排和设置宽高了，所有标签浮动之后不区分行内和块级

- 浮动的元素互相贴靠

  当改变窗口的时候，设置浮动的元素会根据次序和空间自动贴近，如果贴不下就换到下一行去

- 浮动的元素周围的字会像水一样

  标准流中的文字不会被浮动的盒子遮挡住

  > 永远不是一个东西单独浮动，浮动都是一起浮动

- 收缩

  一个浮动的元素如果没有设置width，将自动收缩为内容的宽度

#### 作业

![image-20201226204341675](https://cdn.ethanloo.top/img/20201226204341.png)

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>EthanLoo's</title>
    <link rel="stylesheet" href="./test.css" />
  </head>
  <body>
    <header>
      <div class="header1"></div>
      <div class="header2"></div>
      <div class="header3"></div>
    </header>
    <div class="content">
      <div class="left-content"></div>
      <div class="right-content">
        <div class="main">
          <div class="news">
            <div class="news1"></div>
            <div class="news2"></div>
            <div class="news3"></div>
          </div>
          <div class="hot"></div>
        </div>
        <div class="links"></div>
      </div>
    </div>
    <footer></footer>
  </body>
</html>

```

```css
header {
  margin: 0 auto;
  height: 103px;
  width: 970px;
  margin-bottom: 10px;
}

.header1 {
  float: left;
  height: 103px;
  width: 277px;
  background-color: red;
}

.header2 {
  float: right;
  height: 49px;
  width: 137px;
  background-color: greenyellow;
  margin-bottom: 8px;
}

.header3 {
  float: right;
  height: 46px;
  width: 679px;
  margin-left: 10px;
  background-color: greenyellow;
}

.content {
  margin: 0 auto;
  height: 435px;
  width: 970px;
  margin-bottom: 10px;
}

.left-content {
  height: 435px;
  width: 310px;
  background-color: orange;
  margin-right: 10px;
  float: left;
}

.main {
  float: left;
  height: 400px;
  width: 650px;
  margin-bottom: 10px;
}

.news {
  float: left;
  height: 400px;
  width: 450px;
}

.news1,
.news2,
.news3 {
  width: 450px;
  background-color: skyblue;
  margin-bottom: 10px;
  float: left;
}

.news1 {
  height: 240px;
}

.news2 {
  height: 110px;
}

.news3 {
  height: 30px;
}

.hot {
  float: right;
  background-color: purple;
  width: 190px;
  height: 400px;
}

.links {
  float: right;
  width: 650px;
  height: 25px;
  background-color: green;
}

footer {
  margin: 0 auto;
  height: 35px;
  width: 970px;
  background-color: darkblue;
}

```

### 清除浮动

指清除浮动和浮动之间的影响

1. 加高法

   给浮动元素的祖先元素增加高度

   ```html
   <div>     //设置height
   	<p></p>
   	<p></p>
   	<p></p>
   </div>
   
   <div>    //设置height
   	<p></p>
   	<p></p>
   	<p></p>
   </div>
   ```

2. 给父类加个 `clear:both`

   ```
   <div>
   	<p></p>
   	<p></p>
   	<p></p>
   </div>
   
   <div>   //clear:both;
   	<p></p>
   	<p></p>
   	<p></p>
   </div>
   ```

3. 隔墙法

   在两个浮动元素中间建一个墙（内墙可以让父类自动被撑高）

   ```html
   <div>
   	<p></p>
   	<p></p>
   	<p></p>
   	<div class="cl h10"></div>
   </div>
   
   <div>
   	<p></p>
   	<p></p>
   	<p></p>
   </div>
   ```

4. `overflow:hidden`

   针对每个需要撑高的元素加上该属性

### margin

**margin 塌陷**

标准文档流中，竖直方向的 margin 不叠加，取最大值

**盒子居中**

将 margin 的值设为 auto，表示自动。

当 left, right 都是 auto 的时候，盒子就居中了

```css
margin-left: auto;
margin-right: auto;
```

简写为

```css
margin:0 auto;
```

注意点

1. 只有标准流的盒子才能使用这个居中方法
2. 使用`margin: 0 auto;`的盒子，必须有 width，否则相当于霸占了一行
3. `margin: 0 auto;`只是让盒子居中，文本居中需要使用`text-align: center;`

**善用外层的 padding 而不是里层的margin**

## 定位属性

```css
position: absolute;  <!-- 绝对定位 -->

position: relative;  <!-- 相对定位 -->

position: fixed;     <!-- 固定定位 -->
```

### 相对定位

可以用于盒子的位置的微调

- left：盒子右移

- right：盒子左移

- top：盒子下移

- bottom：盒子上移

```css
position: relative;
left: 50px;
top: 50px;
```

相对定位不脱离标准文档流，因此不会被其他元素挤掉

**用途**

1. 微调元素
2. 做绝对定位的参考

### 绝对定位

定义横纵坐标，原点在父容器的左上角或左下角。横坐标用left表示，纵坐标用top或者bottom表示。

```css
position: absolute;  /*绝对定位*/
left: 10px;  /*横坐标*/
top/bottom: 20px;  /*纵坐标*/
```

绝对定位脱离了标准文档流，所以它可以直接设置宽和高

**参考点**

1. 如果用 top 描述，那么参考点就是**页面的左上角**，不是浏览器的左上角
2. 如果用 bottom 描述，参考点就是**浏览器首屏尺寸对应的左下角**

子绝父相（子元素是绝对定位，父元素是相对定位）是有意义的，可以保证父亲没有脱标，儿子脱标在父亲的范围内移动。

> 工程上会让父亲浮动，相对定位，0偏移，让儿子使用绝对定位

绝对定位的儿子会忽略父类盒子的padding

### 固定定位

相对浏览器窗口进行定位，无论页面如何滚动，这个盒子显示的位置不变

1. 返回到顶部
2. 顶部导航栏

### z-index

定位后的元素可以使用的图层位置，值越大越上层



## CSS3 选择器

**渐进增强策略**

让低版本浏览器能正常访问页面，高版本的浏览器用户体验更好

```css
div 标签选择器

.box 类名选择器

#box　id选择器

div p 后代选择器

div.box 交集选择器

div,p,span 并集选择器

div>p 子代选择器

* : 通配符

div+p: 选中div后面相邻的第一个p

div~p: 选中的div后面所有的p
```

### 属性选择器

属性选择器的标志性符号是`[]`

```
E[属性名=值]
^：开头  $：结尾  *：包含
```

- `E[title]` 选中页面的E元素，并且E存在 title 属性即可。

- `E[title="abc"]`选中页面的E元素，并且E需要带有title属性，且属性值**完全等于**abc。

- `E[attr~=val]`  选择具有 att 属性且属性值为：用空格分隔的字词列表，其中一个等于 val 的E元素。

- `E[attr|=val]` 表示要么是一个单独的属性值，要么这个属性值是以“-”分隔的。

- `E[title^="abc"]` 选中页面的E元素，并且E需要带有 title 属性,属性值以 abc 开头。

- `E[title$="abc"]` 选中页面的E元素，并且E需要带有 title 属性,属性值以 abc 结尾。

- `E[title*="abc"]` 选中页面的E元素，并且E需要带有 title 属性,属性值任意位置包含abc。

### 结构伪类选择器

CSS 中已经有的动态伪类选择器

`:link`、`:active`、`:visited`、`:hover`

CSS3 新增了其他的伪类选择器，其中有通过结构来进行筛选的选择器

- `E:first-child` 匹配父元素的第一个子元素E。

- `E:last-child` 匹配父元素的最后一个子元素E。

- `E:nth-child(n)` 匹配父元素的第n个子元素E。

  > **注意**，盒子的编号是从`1`开始算起，不是从`0`开始算起。

- `E:nth-child(odd)` 匹配奇数

- `E:nth-child(even)` 匹配偶数

- `E:nth-last-child(n)` 匹配父元素的倒数第n个子元素E。

---

- `E:first-of-type` 匹配同类型中的第一个同级兄弟元素E。
- `E:last-of-type` 匹配同类型中的最后一个同级兄弟元素E。
- `E:nth-of-type(n)` 匹配同类型中的第n个同级兄弟元素E。
- `E:nth-last-of-type(n)` 匹配同类型中的倒数第n个同级兄弟元素E。

---

- `E:empty` 匹配没有任何子节点（包括空格等text节点）的元素E。

- `E:target` 匹配相关URL指向的E元素。要配合锚点使用。

### 伪元素选择器

伪元素选择器的标志性符号是 `::`

`E:after`、`E:before `在旧版本里是伪类。CSS3 里，`E:after`、`E:before`会被自动识别为`E::after`、`E::before`，按伪元素来对待，这样做的目的是用来做兼容处理。

- `E::before` 设置在 元素E 前面（依据对象树的逻辑结构）的内容，配合content属性一起使用。

- `E::after` 设置在 元素E 后面（依据对象树的逻辑结构）的内容，配合content属性一起使用。

使用伪元素选择器，可以添加出类似 span 标签的效果，同时这两个属性添加伪元素是行内元素，需要转换成块元素才能设置宽高。

---

- `E::first-letter` 设置元素 E 里面的**第一个字符**的样式。

- `E::first-line` 设置元素 E 里面的**第一行**的样式。

- `E::selection` 设置元素 E 里面被鼠标选中的区域的样式（一般设置颜色和背景色）。



## CSS3 属性

### 文本

**text-shadow：设置文本的阴影**

```
text-shadow: 20px 27px 22px pink;
```

水平位移 垂直位移 模糊程度 阴影颜色

### box-sizing

**外加模式**

```css
box-sizing: content-box;
```

此时设置的 width 和 height 是内容区域的宽高，盒子实际的宽度 = width + padding + border

**内减模式**

```css
box-sizing: border-box;
```

此时设置的 width 和 height 是盒子的总宽高，盒子实际的宽度 = width

### 私有前缀

如果直接这么写，浏览器是不会显示的 🙅‍

```css
background: linear-gradient(left, green, yellow);
```

需要根据浏览器的不同添加前缀

```css
background: -webkit-linear-gradient(left, green, yellow);
background: -moz-linear-gradient(left, green, yellow);
background: -ms-linear-gradient(left, green, yellow);
background: -o-linear-gradient(left, green, yellow);
background: linear-gradient(left, green, yellow);
```

### 边框

**边框圆角**

四个角

```css
border-radius: 60px;
```

单个属性写法

```css
border-top-left-radius: 60px 120px;        //参数解释：水平半径   垂直半径

border-top-right-radius: 60px 120px;

border-bottom-left-radius: 60px 120px;

border-bottom-right-radius: 60px 120px;
```

画圆形的两个方式

```css
/*画圆形的方式一*/
.box:nth-child(1) {
    border-radius: 50px;
}

/*画圆形的方式二*/
.box:nth-child(2) {
    border-radius: 50%;
}
```

**边框阴影**

```css
box-shadow: 水平偏移 垂直偏移 模糊程度 阴影大小 阴影颜色

box-shadow: 15px 21px 48px -2px #666;
```

- 水平偏移：正值向右 负值向左。

- 垂直偏移：正值向下 负值向上。

- 模糊程度：不能为负值。

**边框图片**

单独写

```css
/* 边框图片的路径*/
border-image-source: url("images/border.png");

/* 图片边框的裁剪*/
border-image-slice: 27;

/*图片边框的宽度*/
border-image-width: 27px;

/*边框图片的平铺*/
/* repeat :正常平铺 但是可能会显示不完整*/
/*round: 平铺 但是保证 图片完整*/
/*stretch: 拉伸显示*/
border-image-repeat: stretch;
```

综合属性

```css
border-image: url("images/border.png") 27/20px round;
```

## CSS3 动画

### 过渡

- `transition-property: all;`  如果希望所有的属性都发生过渡，就使用all。

- `transition-duration: 1s;` 过渡的持续时间。

- `transition-timing-function: linear;`  运动曲线。属性值可以是：
  - `linear` 线性
  - `ease`  减速
  - `ease-in` 加速
  - `ease-out` 减速
  - `ease-in-out`  先加速后减速

- `transition-delay: 1s;` 过渡延迟。多长时间后再执行这个过渡动画。

**综合属性**

```css
transition: 让哪些属性进行过度 过渡的持续时间 运动曲线 延迟时间;

transition: all 3s linear 0s;
```

### 2D转换

**缩放**`scale`

```css
transform: scale(x, y);

transform: scale(2, 0.5);
```

参数解释： x：表示水平方向的缩放倍数。y：表示垂直方向的缩放倍数。如果只写一个值就是等比例缩放。y大于1表示放大，小于1表示缩小。

**位移**`translate`

```css
transform: translate(水平位移, 垂直位移);

transform: translate(-50%, -50%);
```

- 参数为百分比，相对于自身移动。

- 正值：向右和向下。 负值：向左和向上。

**位移的应用：让绝对定位中的盒子在父亲里居中**

```css
div {
    width: 600px;
    height: 60px;
    background-color: red;
    position: absolute;       绝对定位的盒子
    left: 50%;               首先，让左边线居中
    top: 0;
    transform: translate(-50%);    然后，利用translate，往左走自己宽度的一半【推荐写法】
```

**旋转**

```css
transform: rotate(角度);

transform: rotate(45deg);
```

参数解释：正值 顺时针；负值：逆时针。

### 3D 旋转

```css
transform: rotateX(360deg);    //绕 X 轴旋转360度

transform: rotateY(360deg);    //绕 Y 轴旋转360度

transform: rotateZ(360deg);    //绕 Z 轴旋转360度
```

