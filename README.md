## Canvas
- canvas: 一般指得是 Html5 标准里面得一个标签
  + 会在页面上出现一个画布
  + 可以再上面进行绘图, 动画, ...
- canvas 技术: 一般是指使用 JS 得 API再 canvas 画布上进行图案得绘制
  + 依靠 JS 来进行绘图
  + 包括 点 线 面 文本 图片 ..., 一切再画布 上得内容都是依靠 JS 添加

### Canvas 画布
+ 一个闭合标签
+ 默认得画布大小是 300 * 150 大小
  - 如果你想调整画布大小, 不能使用 css 得 width 和 height 样式来调整
  - 当使用 css 去调整画布大小得时候, 只是改变了可视得大小
  - 真实得画布大小依旧是 300 * 150
  - 向调整画布大小, 需要直接再标签上使用 width 和 height 属性来进行调整

> 书写canvas的 `width` 和 `height`值的时候, 不需要单位
```js
<canvas width="1400" height="600"> </canvas>
```
+ 标签得兼容性不是很好
  - IE9 以下不兼容
  - 标签对内书写一段文本
  - 会在不支持 canvas 标签得浏览器中显示文本
  - 再支持 canvas 标签得浏览器中不显示文本内容
+ 本质
  - 就是出现一张图片
  - 只不过一个画布是一个空白得图片
  - 我们使用 js 再这个 "图片" 上添加内容而已

### Canvas 引入
1. 获取 canvas 元素
2. 要获取这个元素得 "工具箱"
   - 工具箱里面有很多的 直线工具, 矩形工具, 弧形工具, ...
   - 依赖这些工具箱内的工具进行绘制
   - 我们管这个 工具箱 叫做 `canvas 上下文`
   - 语法: canvas.getContext('2d')
   - 返回值: 一个 canvas 工具箱, 我们可以使用里面得工具进行绘制图形
   
```js
// 写一个canvas标签，并设置宽高
<canvas width="1400" height="600"> </canvas>

// 1. 获取 canvas 元素
const canvas = document.querySelector('canvas')

// 2. 生成一个 canvas 工具箱
const ctx = canvas.getContext('2d')
```