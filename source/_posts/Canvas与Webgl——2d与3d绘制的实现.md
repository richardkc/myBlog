---
title: Canvas与Webgl——2d与3d绘制的实现（不完备）
date: 2019-09-07 10:09:38
tags:
---
### Canvas：聚焦于2d图形，依赖于canvas元素
#### canvas特点
1. canvas除了class、id之类能够定为的属性外只有width和height这两个调控属性；
2. 建议将canvas的width和height定义在标签属性中，使用css定义canvas的width和height之后，绘制出来的图形有可能会是是扭曲的；



### canvas属性
#### 创建环境
1. getContext()：创建一个画布，目前只能支持参数 '2d' ，即创建一个2d绘制环境；

#### 绘制基础图形
##### 固定图形
1. fillRect(x, y, width, height)：绘制一个填充矩形，x，y为焦点，后两个值定义宽高；
2. strokeRect(x, y, width, height)：绘制一个矩形边框，默认长度为1px，但由于我们在选取焦点(x,y)的时候一般取整数值，所以绘制的时候上下左右均会变厚0.5px，这样绘制出来的边框将会是2px的，要防止这样的情况出现，就要将(x,y)的定点具体到 .5 级别；
3. clearRect(x, y, width, height)：绘制一个空白矩形，用来清除；

##### 路径
4. beginPath()：创建绘制路径，无参数；
5. closePath()：关闭当前绘制路径，无参数；调用后会自动闭合beginPath的起点和终点，形成封闭图形；
6. stroke()：同样可关闭当前绘制路径，表示通过线条来绘制，不填充，无参，与closePath的区别在于不链接起点和终点；
7. fill()：同样关闭绘制路径，与closePath的差别在于会填充当前图形，无参；

##### 笔触
8. moveTo(x,y)：将起始笔触起点移动到指定的(x,y)坐标上；
9. lineTo(x,y)：将笔触移动到指定的坐标上，中间形成路径；
10. arc(x, y, radius, startAngle, endAngle, anticlockwise)：绘制一段圆弧；
  x,y为绘制圆弧所在圆上的圆心坐标。radius为半径；
  startAngle以及endAngle参数用弧度定义了开始以及结束的弧度。这些都是以x轴为基准；这两个参数的值为弧度，即范围为0~2*Math.PI；
  参数anticlockwise为一个布尔值。为true时，是逆时针方向，否则顺时针方向；
11. arcTo(x1, y1, x2, y2, radius)：根据给定的控制点和半径画一段圆弧，再以直线连接两个控制点，圆弧在两切线之间；

##### 色彩与不透明度
12. fillStyle=：设置填充色彩值，值可为特殊色彩名、#表示法、rgb()、rgba()；
13. strokeStyle=：设置图形轮廓色彩值，值可为特殊色彩名、#表示法、rgb()、rgba()；
14. globalAlpha=：设置canvas内所有图形的不透明度，值范围为0-1；

##### 线型
15. lineWidth：设置线条宽度，0、负数、Infinity和NaN会被忽略，值可不添加单位，为默认单位；
16. lineCap：设置绘制每一条线段末端的属性，其值有：
  butt：线段末端以方形结束；
  round：线段末端以圆形结束；
  square：线段末端以方形结束，但是增加了一个宽度和线段相同，高度是线段厚度一半的矩形区域，相当于多个一个矩形长度；
17. lineJoin：设置线条与线条间接合处的样式；其值有：
  round：通过填充一个额外的，圆心在相连部分末端的扇形，绘制拐角的形状。 圆角的半径是线段的宽度（即在末端画一个半径为宽度一半的圆）；
  bevel：在相连部分的末端填充一个额外的以三角形为底的区域， 每个部分都有各自独立的矩形拐角（即画出来是平的）；
  miter：通过延伸相连部分的外边缘，使其相交于一点，形成一个额外的菱形区域（即画出来是尖的）；
18. getLineDash：设置为虚线；值须为偶数，如果数组元素的数量是奇数，数组元素会被复制并重复；
19. lineDashOffset：设置虚线偏移量的属性，例如可以实现 “蚂蚁线“ 的效果；



### WebGL：同样依赖canvas元素，可绘制3d图形；