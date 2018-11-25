# 可缩放矢量图形 SVG 入门知识

## SVG

SVG 是一种基于 `XML` 语法的图像格式，全称是`可缩放矢量图`（Scalable Vector Graphics）。其他图像格式都是基于像素处理的，SVG 则是属于`对图像的形状描述`，所以它本质上是`文本文件`，体积较小，且不管放大多少倍都不会失真。

### `<svg>`标签

SVG 代码都放在顶层标签`<svg>`之中。下面是一个例子。

```html
<svg width="100%" height="100%">
  <circle id="mycircle" cx="50" cy="50" r="50" />
</svg>
```
<svg width="100" height="100">
  <circle id="mycircle" cx="50" cy="50" r="50" />
</svg>

`<svg>`的width属性和height属性，指定了 SVG 图像在 HTML 元素中所占据的宽度和高度。除了相对单位，也可以采用绝对单位（单位：像素）。如果不指定这两个属性，SVG 图像默认大小是300像素（宽） x 150像素（高）。

如果只想展示 SVG 图像的一部分，就要指定`viewBox`属性。

```html
<svg width="100" height="100" viewBox="50 50 50 50">
  <circle id="mycircle" cx="50" cy="50" r="50" />
</svg>
```
<svg width="100" height="100" viewBox="50 50 50 50">
  <circle id="mycircle" cx="50" cy="50" r="50" />
</svg>

`<viewBox>`属性的值有四个数字，分别是左上角的横坐标和纵坐标、视口的宽度和高度。上面代码中，SVG 图像是100像素宽 x 100像素高，`viewBox`属性指定视口从(50, 50)这个点开始。所以，实际看到的是右下角的四分之一圆。

注意，视口必须适配所在的空间。上面代码中，视口的大小是 50 x 50，由于 SVG 图像的大小是 100 x 100，所以视口会放大去适配 SVG 图像的大小，即放大了四倍。

如果不指定width属性和height属性，只指定viewBox属性，则相当于只给定 SVG 图像的`长宽比`。这时，SVG 图像的默认大小将等于所在的 HTML 元素的大小。


## 基本的 SVG 图形

### 1. 矩形 rect

```html
<svg width="500" height="100">
	<rect x="0" y="0" width="100" height="20" />
</svg>
```
<svg width="500" height="50">
	<rect x="0" y="0" width="100" height="20" />
</svg>

属性：
- x：矩形左上角的横坐标
- y：矩形左上角的纵坐标
- width：矩形的宽度
- height：矩形的高度


### 2. 圆角矩形 rect

```html
<svg width="500" height="80">
	<rect x="0" y="20" width="100" height="20" rx="10" ry="15"/>
</svg>
```
<svg width="500" height="80">
	<rect x="0" y="20" width="100" height="20" rx="10" ry="15"/>
</svg>

属性：
- rx：圆角水平方向上的曲率半径
- ry：圆角垂直方向上的曲率半径

### 3. 圆形 circle

```html
<svg width="500" height="100">
	<circle cx="100" cy="50" r="20"/>
</svg>
```
<svg width="500" height="100">
	<circle cx="100" cy="50" r="20"/>
</svg>

属性：
- cx：圆心的横坐标
- cy：圆心的纵坐标
- r：圆的半径

### 4. 椭圆 ellipse

```html
<svg width="500" height="100">
	<ellipse cx="100" cy="150" rx="40" ry="20" />
</svg>
```
<svg width="500" height="100">
	<ellipse cx="100" cy="50" rx="40" ry="20" />
</svg>

属性：
- cx：椭圆中心点的横坐标
- cy：椭圆中心点的纵坐标
- rx：椭圆水平方向上的半径
- ry：椭圆垂直方向上的半径


### 5. 线 line

```html
<svg width="500" height="100">
	<line x1="0" y1="30" x2="200" y2="80" stroke="blue" />
</svg>
```
<svg width="500" height="100">
	<line x1="0" y1="30" x2="200" y2="80" stroke="blue" />
</svg>


属性：
- x1：线条起点的横坐标
- x2：线条终点的横坐标
- y1：线条起点的纵坐标
- y2：线条终点的纵坐标
- stroke：描边的颜色

**注意**：为了让线条可见，必须设置 `stroke` 的颜色。

### 6. 折线 polyline

```html
<svg width="500" height="200">
	<polyline points="50,120 150,80 300,150 350,120" fill="none" stroke="black" />
</svg>
```
<svg width="500" height="200">
	<polyline points="50,150 150,80 300,150 350,120" fill="none" stroke="black" />
</svg>

属性：
- points：指定了每个端点的坐标，横坐标与纵坐标之间用`逗号`分隔，点与点之间用`空格`分隔。
- fill: 填充的颜色
- stroke: 描边的颜色

### 7. 多边形 polygon

```html
<svg width="500" height="200">
	<polygon points="100,0 150,50 250,50, 250,0" />
</svg>
```
<svg width="500" height="200">
	<polygon points="100,0 150,50 250,50, 250,0" />
</svg>

属性：
- points：指定了每个端点的坐标，横坐标与纵坐标之间用逗号分隔，点与点之间用空格分隔。

**注意**： 多边形 polygon 是一个封闭的图形，指定的最后一个点会自动与第一个点相连。

### 8. 路径 path 
```html
<svg width="500" height="100">
	<path d="M 18,3 L 46,3 L 46,40 L 61,40 L 32,68 L 3,40 L 18,40 Z"></path>
</svg>
```
<svg width="500" height="100">
	<path d="M 18,3 L 46,3 L 46,40 L 61,40 L 32,68 L 3,40 L 18,40 Z"></path>
</svg>

属性 d: 表示绘制顺序，它的值是一个长字符串，每个字母表示一个绘制动作，后面跟着坐标。

- M：移动到（moveto）
- L：画直线到（lineto）
- Z：闭合路径

### 9. 其他 SVG 标签元素

#### 9.1. `<text>` 文本标签
```html
<svg width="300" height="50">
  <text x="50" y="25">Hello World</text>
</svg>
```
<svg width="300" height="50">
  <text x="50" y="25">Hello World</text>
</svg>

属性：
- x： 表示文本区块基线（baseline）起点的横坐标
- y： 表示文本区块基线（baseline）起点的纵坐标

#### 9.2 `<g>`标签
`<g>`标签用于将多个形状组成一个组（group），方便复用。

```html
<svg width="300" height="100">
  <g id="myCircle">
    <text x="25" y="20">圆形</text>
    <circle cx="50" cy="50" r="20"/>
  </g>

  <use href="#myCircle" x="100" y="0" fill="blue" />
  <use href="#myCircle" x="200" y="0" fill="white" stroke="blue" />
</svg>
```

<svg width="300" height="100">
  <g id="myCircle">
    <text x="25" y="20">圆形</text>
    <circle cx="50" cy="50" r="20"/>
  </g>

  <use href="#myCircle" x="100" y="0" fill="blue" />
  <use href="#myCircle" x="200" y="0" fill="white" stroke="blue" />
</svg>

##### 9.3 `<defs>`标签

`<defs>`标签用于自定义形状，它内部的代码不会显示，仅供引用。

```html
<svg width="300" height="100">
  <defs>
    <g id="myCircle">
      <text x="25" y="20">圆形</text>
      <circle cx="50" cy="50" r="20"/>
    </g>
  </defs>
  <use href="#myCircle" x="0" y="0" />
  <use href="#myCircle" x="100" y="0" fill="blue" />
  <use href="#myCircle" x="200" y="0" fill="white" stroke="blue" />
</svg>
```
<svg width="300" height="100">
  <defs>
    <g id="myCircle">
      <text x="25" y="20">圆形</text>
      <circle cx="50" cy="50" r="20"/>
    </g>
  </defs>
  <use href="#myCircle" x="0" y="0" />
  <use href="#myCircle" x="100" y="0" fill="blue" />
  <use href="#myCircle" x="200" y="0" fill="white" stroke="blue" />
</svg>

##  SVG 元素的样式属性

### 颜色和透明度

#### 颜色

在 SVG 中，有多种方式设置 fill（填充） 和 stroke（描边） 的颜色：颜色关键字, HEX, RGB, RGBA等。
```html
<svg width="500" height="100">
  <circle cx="50" cy="50" r="20" fill="black" stroke="red" />
  <circle cx="100" cy="50" r="20" fill="#f0f" stroke="#000"/>
  <circle cx="150" cy="50" r="20" fill="rgb(125,139,30)"  stroke="rgb(0,255,0)"/>
  <circle cx="200" cy="50" r="20" fill="rgba(125,139,30,0.5)" stroke="rgba(0,255,0,0.5)"/>
</svg>
```
<svg width="500" height="100">
  <circle cx="50" cy="50" r="20" fill="black" stroke="red" />
  <circle cx="100" cy="50" r="20" fill="#f0f" stroke="#000"/>
  <circle cx="150" cy="50" r="20" fill="rgb(125,139,30)"  stroke="rgb(0,255,0)"/>
  <circle cx="200" cy="50" r="20" fill="rgba(125,139,30,0.5)" stroke="rgba(0,255,0,0.5)"/>
</svg>

#### 透明度：

对 SVG 图形进行透明化处理

- opacity: 用于设置 fill 和 stroke 的透明度
- fill-opacity: 只用于设置 fill （填充）的透明度
- stroke-opacity: 只用于设置 stroke （描边） 的透明度
- RGBA: 带 alpha 透明通道值的 RGB 颜色

```html
<svg width="500" height="100">
	<circle cx="50" cy="50" r="20" fill="rgb(125,139,30)" stroke="black"/>
	<circle cx="100" cy="50" r="20" fill="rgb(125,139,30)" opacity="0.5" stroke="black"/>
	<circle cx="150" cy="50" r="20" fill="rgb(125,139,30)" stroke="black" stroke-opacity="0.5"/>
	<circle cx="200" cy="50" r="20" fill="rgb(125,139,30)" fill-opacity="0.5" stroke="black" stroke-opacity="0.5"/>
	<circle cx="250" cy="50" r="20" fill="rgba(125,139,30,0.5)" stroke="black" />
	<circle cx="300" cy="50" r="20" fill="rgba(125,139,30,0.5)" stroke="black" stroke-opacity="0.5" />
</svg>

```
<svg width="500" height="100">
	<circle cx="50" cy="50" r="20" fill="rgb(125,139,30)" stroke="black"/>
	<circle cx="100" cy="50" r="20" fill="rgb(125,139,30)" opacity="0.5" stroke="black"/>
	<circle cx="150" cy="50" r="20" fill="rgb(125,139,30)" stroke="black" stroke-opacity="0.5"/>
	<circle cx="200" cy="50" r="20" fill="rgb(125,139,30)" fill-opacity="0.5" stroke="black" stroke-opacity="0.5"/>
	<circle cx="250" cy="50" r="20" fill="rgba(125,139,30,0.5)" stroke="black" />
	<circle cx="300" cy="50" r="20" fill="rgba(125,139,30,0.5)" stroke="black" stroke-opacity="0.5" />
</svg>


使用 SVG 绘图时，建议使用 `opacity` 而不是 RGBA。这样代码可读性更强，一眼就能分辨出哪些元素是透明的。另外，在 D3.js 中，可以通过修改 opacity 的值来改变透明度，而不用同时改变 颜色的值。

#### 描边：

对于 描边 stroke， 我们可以设置它的 颜色、宽度、透明度、端点

- stroke: 描边颜色
- stoke-width: 描边的宽度
- stroke-opacity: 描边的透明度
- stroke-lincap: 描边的端点的形状。默认 butt, round 圆角，square 矩形。
- stroke-dasharray:  控制用来描边的点划线的图案范式。

### 通过 CSS 设置 SVG 元素的样式

CSS 只能用来设置`样式属性`，比如 fill, stroke 等，不能用于定义 SVG 元素的 `位置`和`尺寸`。


## 变形 

通过设置变形属性， SVG 元素可以被移动、旋转及操控。

- translate(tx[, ty]): 重新定义SVG 元素的坐标系统, ty 默认为0。
- rotate(angle[, cx, cy])：按顺时针方向旋转元素，角度等于 angle, cx和cy 定义了元素旋转所围绕的中心点，默认为（0,0）。
- scale(sx[, sy]): 按水平方向系数sx 和垂直方向系数sy 缩放元素。如果sy未定义，则其值和sx相同，及等比缩放。

##### 参考资料：

[MDN SVG 文档](https://developer.mozilla.org/en-US/docs/Web/SVG)

[Visual Storytelling with D3](http://ritchiesking.com/book/)

[SVG 图像入门教程 by 阮一峰](http://www.ruanyifeng.com/blog/2018/08/svg.html)

