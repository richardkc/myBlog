---
title: css之flex
date: 2019-09-03 13:56:40
tags: css3
---
### flex六属性
#### justify-content
1. flex-start: 弹性盒子元素将向行起始位置对齐。第一个元素与左起始边界对齐，后面的元素接着第一个元素进行排列。

2. flex-end: 弹性盒子元素将向行结束位置对齐。整体靠着行结束的位置排列。

3. center：整体居中显示。

4. space-between: 弹性盒子元素均匀分布。第一个元素的边界与行的主起始位置的边界对齐，同时最后一个元素的边界与行的主结束位置的边距对齐，而剩余的伸缩盒项目则平均分布，并确保两两之间的空白空间相等。

5. space-around: 弹性盒子元素均匀分布。两端保留子元素与子元素之间间距大小的一半。

#### align-items
**决定了弹性盒水平/垂直分布时在侧轴（垂直/水平）方向上的伸缩情况**
1. flex-start：向侧轴开始方向对齐，即弹性盒子堆积到边框顶部；

2. flex-end：向侧轴结束方向对齐；

3. center：在侧轴居中；

4. stretch（默认值）：弹性盒拉伸到两端接触侧轴开始和结束点，即如果项目未设置高度或高度设为auto，将占满整个容器；

5. baseline：项目第一行文字的基线对齐；  

#### align-content
**容器在侧轴方向上有额外空间时，如何每排布一行，要多行时才有作用**
1. flex-start：侧轴开始方向对齐；

2. flex-end：侧轴结束方向对齐；

3. center：侧轴中心中对齐；

4. space-between：与侧轴两端对齐，每行轴线间隔平均；

5. space-around：每根轴线两侧间隔相等；

6. stretch（默认值）：占满整个整个侧轴；

#### flex-direction
1. row（默认值）：水平排列，起点在左边；

2. row-reverse：水平排列，起点在右边；

3. column：垂直排列，起点在顶部；

4. column：垂直排列，起点在底部；

#### flex-wrap
**flex在第一行排不下之后的设置**
1. nowrap（默认值）：不换行；

2. wrap：换行，第二行在第一行下面，水平排列方式同第一行；

3. wrap-reverse：换行，第二行在第一行上面，水平排列方式同第一行；

#### flex-flow
为flex-direction和flex-wrap的缩写，同时又两个值，默认值为row和wrap；

#### flex-basis
定义初始盒子的大小，有auto、0之类的具体数值；

#### flex-grow
定义盒子的拉伸因子；

### flex-shrink
定义盒子的收缩因子；

