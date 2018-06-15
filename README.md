# Canvas 基础

学习 Canvas 基础用法时的一些总结和 Demo。

学习资源：[anvas: Draw on the web](https://yuque.com/airing/canvas/readme)

## 基础知识

`<canvas>` 标签在页面上定义了一个画布，提供了丰富的 JS API 来绘制图形。它本身只是一个容器，和其他 HTML 元素一样，可以添加属性、设置样式等。

在 canvas 上绘制，需要先获取到相应的 DOM，然后获取到相应的绘制上下文，接着利用上下文的 API 完成绘制。

获取画笔(2D)：`canvas.getContext("2d");`，当前唯一的合法值是 "2d"，它指定了二维绘图，在未来，如果 `<canvas>` 标签扩展到支持 3D 绘图，getContext() 方法可能允许传递一个 "3d" 字符串参数。