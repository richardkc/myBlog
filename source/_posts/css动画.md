---
title: css动画
date: 2019-09-06 20:21:27
tags: css3
---
### transition
1. transition-delay：设置动画延迟，单位为s或ms；

2. transition-duration：设置动画运行持续时间，单位为s或ms；

3. transition-property：设置指定动画名；

4. transition-timing-function：设置动画运行速度的函数关系，具体数值有ease，ease-in，ease-out，ease-in-out等，具体参数可以google；

5. transition：是以上方法的缩写集合，具体顺序为：transition-property，transition-duration，transition-timing-function，transition-delay ；



### transform
1. backface-visibility：设置3d元素的背面朝向观察者时是否可见，值为visible（可见）和hidden（隐藏）；

2. perspective：设置观察者与 z=0 平面的距离，使具有三维位置变换的元素产生透视效果（有让元素贴近观察者的视觉效果）；

3. perspective-origin：设置观察者的位置，用作perspective 属性的消失点（视觉效果就是从填写值的方向位置进行观察）
  该属性值有：**x-position和y-position，范围从0到100%，可为负值**。特殊值有：center(50%,50%)，top（y-position=0），bottom（y-position=100%），left（x-position=0），right（x-position=100%），top-left等；

4. rotate：3d旋转，参数为 (x,y,z,deg) （xyz均为向量值，实际旋转角度为向量值*deg）；单值单位可为：**deg、turn、rad**，此时为2d旋转；

5. scale：独立指定CSS属性 transform 缩放的比例；
  单值情况：同时作用于x轴和y轴，为2d缩放；
  双值情况：分别定义x轴和y轴的缩放情况，同为2d缩放，值可为数值或百分比；
  三值情况：分别定义x轴、y轴、z轴的缩放情况，为3d缩放，此时相当于scale3d()属性；

6. translate：定义transform的平移，数值可为具体像素值或百分比；
  单值情况：同时定义x轴和y轴上的平移，为2d；
  双值情况：分别定义x轴和y轴上的平移，为2d；
  三值情况：分别定义x轴、y轴、z轴上的平移，为3d，此时相当于translate3d()属性；
  无平移：none；

7. transform-origin：设置一个元素变形的焦点（原点）；
  单值情况：为具体长度或是left, center, right, top, bottom中一个，为平面原点；
  双值情况：两个均可为数值，或者第一个参数为left，center，right中任意一个，第二个参数为top，center，bottom中任意一个，为平面原点；
  三值情况：前两个值的设置与双值情况相同，第三个值必须为数值长度，此时为立体原点；

8. transform-style：设置元素是否处于同个3d平面（即有可能会造成交叉），值为flat（相互独立），preserve-3d（可交叉）；

9. skew：设置元素在2D平面上一个对象的歪斜变换；其值有：
  单ax：表示要用于沿横坐标扭曲元素的角度；
  ax、ay：ay表示用于沿纵坐标扭曲元素的角度。如果未定义，则其默认值为0，导致纯水平倾斜。

10. transform：集合属性；通过如 transform:scale() 这样的写法来实现所有属性的控制；除了上述部分属性之外，transform还有一些特定的函数，具体需查看文档或者google学习：
  skew：该函数会使得在每个方向上扭曲元素上的每个点以一定角度。这是通过将每个坐标增加一个与指定角度成比例的值和到原点的距离来完成的。离原点越远，拉伸的值就越大；具体参数有 (ax,ay) ，两个值均为角度；
  matrix（矩阵）：matrix(a, b, c, d, tx, ty)；
  matrix3d：matrix3d(a1, b1, c1, d1, a2, b2, c2, d2, a3, b3, c3, d3, a4, b4, c4, d4)等；

11. **transform一般用来设置静态页面，要实现动画得与另外的属性嵌套使用**



### animation
1. animation-delay：设置animation的延迟时间，单位为s或ms；

2. animation-direction：设置动画是否反向播放；其值有：
  normal：默认值，每个动画结束时重置到起点重新开始；
  alternate：动画交替反向运行，反向运行时，动画按步后退，同时，带时间功能的函数也反向，比如，ease-in 在反向时成为ease-out；
  reverse：反向运行动画，每周期结束动画由尾到头运行；
  alternate-reverse：反向交替， 反向开始交替；

3. animation-duration：设置动画运行周期的时长；

4. animation-iteration-count：设置动画结束前运行的次数；其值有：
  infinite：无线循环；
  （number）：具体数值，如1表示播放一次；

5. animation-fill-mode：设置CSS动画在执行之前和之后如何将样式应用于其目标；其值有：
  none：无设置；
  forward：目标将保留由执行期间遇到的最后一个关键帧计算值。 最后一个关键帧取决于animation-direction和animation-iteration-count的值，具体可查看mdn文档；
  backward：动画将在应用于目标时立即应用第一个关键帧中定义的值，并在animation-delay期间保留此值。 第一个关键帧取决于animation-direction的值，具体查看mdn文档；
  both：动画将遵循forwards和backwards的规则，从而在两个方向上扩展动画属性，即同时具有forward和backward的特点；

6. animation-name：设置应用的一系列动画，每个名称代表一个由@keyframes定义的动画序列，可同时创建多个，值为none时表示无关键帧；

7. animation-play-state：表示动画当前是否正在运行，值有running和paused；

8. animation-time-function：设置动画运行的速度函数，有ease、ease-in等，具体参考mdn和google；

9. animation：前面所有属性的集合使用，值的顺序为 animation-name，animation-duration, animation-timing-function，animation-delay，animation-iteration-count，animation-direction，animation-fill-mode，animation-play-state；

10. **animation能通过@keyframe xxx{x%{} y%{}...}连用，这也是跟transition的不同之处，transition一般跟伪属性连用，只能设置头尾**