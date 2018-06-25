# Canvas 基础

学习 Canvas 基础用法时的一些总结和 Demo。

学习资源：[anvas: Draw on the web](https://yuque.com/airing/canvas/readme)

## 基础知识

`<canvas>` 标签在页面上定义了一个画布，提供了丰富的 JS API 来绘制图形。它本身只是一个容器，和其他 HTML 元素一样，可以添加属性、设置样式等。

在 canvas 上绘制，需要先获取到相应的 DOM，然后获取到相应的绘制上下文，接着利用上下文的 API 完成绘制。

获取画笔(2D)：`canvas.getContext("2d");`，当前唯一的合法值是 "2d"，它指定了二维绘图，在未来，如果 `<canvas>` 标签扩展到支持 3D 绘图，getContext() 方法可能允许传递一个 "3d" 字符串参数。

**Canvas是基于状态的绘制，意思是先设置画笔的各种状态，绘制路径等，然后执行绘制的方法进行绘制，如果多次调用绘制函数，之前设置的状态会被保留并且可以被覆盖。**

## 线段

### 移动画笔(moveTo())

`context.moveTo()`，将画笔移动到指定坐标。记住，这里是以 canvas 画布的左上角为笛卡尔坐标系的原点，且y轴的正方向向下，x轴的正方向向右。

### 笔画停点(lineTo())

同理，context.lineTo(600,600)。这句的意思是从 上一笔的停止点 绘制到(600,600)这里。

### 设置画笔属性

`context.lineWidth = 5`，这句话的意思是设置画笔(线条)的粗细为 5 px。
`context.strokeStyle = "#AA394C"`，这句话的意思是设置画笔(线条)的颜色为玫红色。

### 绘制

确定绘制只有两种方法，`fill()` 和 `stroke()`，前者是指填充，后者是指描边。

### 使用 beginPath() 开始绘制

为了让绘制方法不重复绘制，我们可以在每次绘制之前加上 `beginPath()`，代表下次绘制的起始之处为 `beginPath()` 之后的代码。

### 使用closePath()闭合图形

绘制路径的时候需要将规划的路径使用 `beginPath()` 与 `closePath()` 包裹起来。当然，最后一笔可以不画出来，直接使用`closePath()`，它会自动帮你闭合的。(所以如果你不想绘制闭合图形就不可以使用 `closePath()`)

### 使用rect()方法绘制矩形

由于绘制矩形是常用的方法，所以在Canvas API中已经帮我们封装好了一个绘制矩形的方法——rect()。这个方法接收4个参数x, y, width, height，实际调用时也就是 `context.rect(x,y,width,height);`

### 线条属性概述

#### lineCap

lineCap 定义上下文中线的端点，可以有以下 3 个值。
- butt：默认值，端点是垂直于线段边缘的平直边缘。
- round：端点是在线段边缘处以线宽为直径的半圆。
- square：端点是在线段边缘处以线宽为长、以一半线宽为宽的矩形。

#### lineJoin

lineJoin 定义两条线相交产生的拐角，可将其称为连接。在连接处创建一个填充三角形，可以使用 lineJoin 设置它的基本属性。

- miter：默认值，在连接处边缘延长相接。miterLimit 是角长和线宽所允许的最大比例(默认是 10)。
- bevel：连接处是一个对角线斜角。
- round：连接处是一个圆。


#### 线宽

lineWidth 定义线的宽度(默认值为 1.0)。

#### 笔触样式

strokeStyle 定义线和形状边框的颜色和样式。
