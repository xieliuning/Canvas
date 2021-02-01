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

### Canvas API

#### 颜色、样式和阴影
|  属性  | 描述  |  
|  ----  | ----  |  
| fillStyle  | 	设置或返回用于填充绘画的颜色、渐变或模式。 |
| strokeStyle  | 	设置或返回用于笔触的颜色、渐变或模式。 |   
| shadowColor | 	设置或返回用于阴影的颜色。 |  
| shadowBlur | 	设置或返回用于阴影的模糊级别。 | 
| shadowOffsetX | 	设置或返回阴影与形状的水平距离。 |
| shadowOffsetY | 	设置或返回阴影与形状的垂直距离。 |  


|  方法  | 描述  |  
|  ----  | ----  |  
| createLinearGradient()  | 	创建线性渐变（用在画布内容上）。 |
| createRadialGradient()  | 	创建放射状/环形的渐变（用在画布内容上）。 |  

#### 线条样式
|  属性  | 描述  |  
|  ----  | ----  |  
| lineCap  | 	设置或返回线条的结束端点样式。 |
| lineJoin  | 	设置或返回两条线相交时，所创建的拐角类型。 |   
| lineWidth | 	设置或返回当前的线条宽度。 |  

#### 矩形
|  方法  | 描述  |  
|  ----  | ----  |  
| rect()  | 		创建矩形。 |
| fillRect()  | 	绘制"被填充"的矩形。 |   
| strokeRect() | 	绘制矩形（无填充）。 |  
| clearRect() | 	在给定的矩形内清除指定的像素。 |  

#### 路径
|  方法  | 描述  |  
|  ----  | ----  |  
| fill()  | 		填充当前绘图（路径）。 |
| stroke()  | 	绘制已定义的路径。 |   
| beginPath() | 		起始一条路径，或重置当前路径。 |  
| moveTo() | 		把路径移动到画布中的指定点，不创建线条。 |  
| closePath() | 		创建从当前点回到起始点的路径。 |  
| lineTo() | 		添加一个新点，然后在画布中创建从该点到最后指定点的线条。 |  
| clip() | 			从原始画布剪切任意形状和尺寸的区域。 |  
| quadraticCurveTo() | 		创建二次贝塞尔曲线。 |  
| bezierCurveTo() | 		创建三次贝塞尔曲线。 |  
| arc() | 		创建弧/曲线（用于创建圆形或部分圆）。 |  
| arcTo() | 		创建两切线之间的弧/曲线。 |  

#### 转换
|  方法  | 描述  |  
|  ----  | ----  |  
| scale()  | 		缩放当前绘图至更大或更小。 |
| rotate()  | 	旋转当前绘图。 |   
| translate() | 	重新映射画布上的 (0,0) 位置。 |  

#### 文本
|  属性  | 描述  |  
|  ----  | ----  |  
| font  | 		设置或返回文本内容的当前字体属性。 |
| textAlign  | 		设置或返回文本内容的当前对齐方式。 |   
| textBaseline | 		设置或返回在绘制文本时使用的当前文本基线。 |

|  方法  | 描述  |  
|  ----  | ----  |  
| fillText()  | 			在画布上绘制"被填充的"文本。 |
| strokeText()  | 			在画布上绘制文本（无填充）。 |  

#### 图像绘制
|  方法  | 描述  |  
|  ----  | ----  |  
| drawImage()  | 		向画布上绘制图像、画布或视频。 |

#### 像素操作
|  属性  | 描述  |  
|  ----  | ----  |  
| width  | 		返回 ImageData 对象的宽度。 |
| height  | 		返回 ImageData 对象的高度。 |   
| data | 			返回一个对象，其包含指定的 ImageData 对象的图像数据。 |

|  方法  | 描述  |  
|  ----  | ----  |  
| createImageData()  | 		创建新的、空白的 ImageData 对象。 |
| getImageData()  | 			返回 ImageData 对象，该对象为画布上指定的矩形复制像素数据。 |   
| putImageData() | 			把图像数据（从指定的 ImageData 对象）放回画布上。 |

### Canvas 案例
#### 绘制平行线
canvas 绘制一个不一样颜色得平行线
  + 第一条线 宽度 4px, 颜色 红色
  + 第二条线 宽度 6px, 颜色 蓝色
  + 当你想让两条线出现不一样得样式得时候
    - 你需要再画第二条线得时候
    - 告诉 canvas 我是从新开启得一条线, 和之前得没有关系
    - 不然的话, 颜色和宽度会根据上下文进行继承
  + 开启一条新的线
    - 再你 `moveTo` 之前告诉 canvas
    - 语法: `ctx.beginPath()`
    - 注意: 开启新的线以后, 如果你不单独设置样式
      - 依旧会继承上面设置过的
      - 但是你一旦单独设置了样式以后, 只会影响这条线以后得内容
      - 不会影响之前得内容了

```js
// 1. 获取 canvas 元素
const canvas = document.querySelector('canvas')

// 2. 生成一个 canvas 工具箱
const ctx = canvas.getContext('2d')


// 3-1. 绘制第一条线

// 给第一条线设置宽度和颜色
ctx.lineWidth = 4
ctx.strokeStyle = 'red'
ctx.moveTo(100, 100)
ctx.lineTo(200, 100)
ctx.stroke()

// 3-2. 绘制第二条线
// 重新把笔移动到第二条线得开始位置

// 给第二条线设置宽度和颜色
// 需要告诉 canvas 我要开启一条新的线, 不要和上面得一样
ctx.beginPath()
ctx.lineWidth = 6
ctx.strokeStyle = 'skyblue'
ctx.moveTo(100, 200)
ctx.lineTo(200, 200)
ctx.stroke()
```

#### 绘制三角形
闭合图形
  1. 自己书写所有线段, 回到起点
    - 手动闭合
  2. 依靠 canvas 工具箱来帮我们闭合
    - 自动闭合
    - 语法: `ctx.closePath()`
    - 会自动把闭合点得角补齐
  3. 可以依靠填充得方式进行补齐
    - 不再对路径进行描边, 而是进行填充
    - 语法: `ctx.fill()`
  + 注意: 描边和填充可以一起使用
    - 注意, 描边有描边得规则
      - `strokeStyle`, 设置描边得颜色
    - 填充有填充得规则
      - `fillStyle` 设置填充颜色

```js
// 1. 获取 canvas 元素
const canvas = document.querySelector('canvas')

// 2. 生成一个 canvas 工具箱
const ctx = canvas.getContext('2d')

// 3. 绘制三角形
// 3-0. 把线变得宽一些
ctx.lineWidth = 10

// 补充描边规则
ctx.strokeStyle = 'red'

// 补充填充颜色
ctx.fillStyle = 'skyblue'

// 3-1. 把 笔 移动到起点
ctx.moveTo(100, 100)
// 3-2. 绘制第一个直角边
ctx.lineTo(250, 100)
// 3-3. 绘制第二个直角边
ctx.lineTo(250, 250)
// 3-4. 回到起点(手动闭合方式)
// ctx.lineTo(100, 100)
// 3-4. 回到起点(自动闭合方式)
ctx.closePath()

// 3-5. 进行描边
ctx.stroke()

// 3-5. 进行填充
ctx.fill()

```

#### 绘制矩形
1. 绘制矩形, 给一个起点坐标
  + 加上一个矩形得宽和高
  + 语法: `ctx.rect(startX, startY, width, height)`
    - startX: 矩形起点得 X 轴坐标
    - startY: 矩形起点得 Y 轴坐标
    - width: 矩形得宽度
    - height: 矩形得高度
  + 注意: 绘制得依旧是路径

2. 直接绘制描边矩形
  + 语法: `ctx.strokeRect(startX, startY, width, height)`

3. 直接绘制一个填充矩形
  + 语法: `ctx.fillRect(startX, startY, width, height)`
  
4. 需求:     
  + 绘制两个矩形, 一个红色 一个蓝色, 填充颜色
    - 不需要开启新的路径
    - 因为 fillStyle 不会相互影响   
  + 绘制两个矩形, 一个红色 一个蓝色, 描边颜色
    - 绘制描边矩形也不需要开启新的路径
    - 因为你不是根据路径闭合出现得矩形
    - 位是直接出现得矩形

5. 清除矩形
  + 把一段矩形位置得东西清空
  + 语法: `ctx.clearRect(startX, startY, width, height)`

#### 绘制填充渐变颜色
canvas 绘制填充渐变颜色
  + 开始颜色   red
  + 结束颜色   skyblue
  + 距离
  + 注意: 
    - **fill 可以设置渐变方案**
    - **stroke 页能设置渐变方案**

步骤
  1. 确定渐变方案
  2. 把你的渐变方案赋值给 fillStyle
  3. 再形状填充得时候使用 fillStyle 进行填充
  + 注意: 渐变方案和形状没有关系
    => 方案就是根据画布来计算得尺寸

1. 确定渐变方案
  + 语法: `ctx.createLinearGradient(startX, startY, endX, endY)`
  + 语法: 添加渐变颜色
    => 渐变方案.addColorStop(数字, 颜色)
    => 数字: 0 ~ 1, 0 表示开始 1 表示结束

```js
const canvas = document.querySelector('canvas')
const ctx = canvas.getContext('2d')

// 1. 确定一个渐变方案
//     确定好了渐变得方向和距离
const linearGradient = ctx.createLinearGradient(500, 100, 100, 100)
//     添加渐变颜色
linearGradient.addColorStop(0, 'red')
linearGradient.addColorStop(1, 'skyblue')

// 2. 给填充赋值
//    渐变方案是可以直接赋值使用得
ctx.fillStyle = linearGradient

// 3. 绘制一个填充矩形
ctx.fillRect(100, 100, 400, 250)
```


#### 绘制圆弧
canvan 画一个 60 弧线

1. 确定圆心位置
2. 生成弧线路径
  - 语法: `ctx.arc(circleX, circleY, radius, startArc, endArc, direction)`
    - `circleX`: 表示弧线得圆心 X 轴坐标
    - `circleY`: 表示弧线得圆心 Y 轴坐标
    - `radius`: 表示弧线得圆形半径
    - `startArc`: 表示起点弧度
    - `endArc`: 表示终点弧度
    - `direction`: 表示弧线方向
      - 默认是 `false` 表示顺时针
      - 选填是 `true` 表示逆时针

```js
const canvas = document.querySelector('canvas')
const ctx = canvas.getContext('2d')

// 1. 确定圆心位置
const width = ctx.canvas.width
const height = ctx.canvas.height
const x = width / 2
const y = height / 2
// 1-2. 确定一下圆半径得大小
const r = 100

// 2. 开始画弧线
// 2-1. 确定起点和终点得 弧度
const startArc = 0
const endArc = Math.PI / 180 * 90

// 2-2. 开始绘制弧线路径
ctx.moveTo(x, y)
ctx.arc(x, y, r, startArc, endArc)

// 自动闭合
ctx.closePath()

// 3. 描边
ctx.stroke()

ctx.fill()


// 4. 画一个弧线
ctx.beginPath()
// // 4-1. 确定起点和终点得 弧度
const startArc2 = Math.PI / 180 * 120
const endArc2 = Math.PI / 180 * 180
ctx.arc(x, y, r, startArc2, endArc2)
ctx.stroke()
```