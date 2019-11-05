---
title: 有趣的background
date: 2019-09-08 14:01:39
tags:
---
### background
1. background：所有属性的缩写，顺序为：background-clip、background-color、background-image、background-origin、background-position、background-repeat、background-size和background-attachment；

2. background-attachment：决定背景图像的位置是在视口内固定，还是随着包含它的区块滚动；其值有：
  fixed：此关键字表示背景相对于视口固定。即使一个元素拥有滚动机制，背景也不会随着元素的内容滚动；
  local：此关键字表示背景相对于元素的内容固定。如果一个元素拥有滚动机制，背景将会随着元素的内容滚动；
  scroll：此关键字表示背景相对于元素本身固定， 而不是随着它的内容滚动；

3. background-clip ：设置元素的背景（背景图片或颜色）是否延伸到边框下面，其值有：
  border-box：包括border和padding；
  padding-box：包括padding不包括border；
  content-box：不包括border和padding；
  text：嵌套给文字，视觉效果就像是文字镂空，底图为背景；

4. border-color：设置背景颜色；

5. border-image：设置背景为图片，值有none、inherit和图片的  **url()** ；

6. background-origin 规定了指定背景图片background-image 属性的原点位置的背景相对区域，一般和后面的background-position联用， **（当background-attachment为fixed时无效）* ；其值有：
  border-box，padding-box，content-box，分别以border、padding和content为参考；

7. background-position：为每一个背景图片设置初始位置。 这个位置是相对于由 background-origin 定义的位置图层的；其值有：
  单值：center、left、right、top、bottom；
  双值：一般为百分比或像素值，第一个值为left的值，第二个为top的值；
  四值：1,3为top、bottom、left、right任一； 2,4为像素值或百分比；1,2和3,4分别对应；

8.  background-repeat：定义背景图像的重复方式。背景图像可以沿着水平轴，垂直轴，两个轴重复，或者根本不重复；此处只列举单值情况，双值情况上mdn文档查看：
  repeat-x、repeat-y：在x轴/y轴上无间隔重复；
  repeat：在全范围内重复，相当于上两个值合并；
  no-repeat：无重复，默认值；
  **round：这个属性会造成图片拉伸、压缩，暂时也没有看到别的用途，乱七八糟的个人不建议使用；*

9. background-size：设置背景图片大小。图片可以保有其原有的尺寸，或者拉伸到新的尺寸，或者在保持其原有比例的同时缩放到元素的可用空间的尺寸；其值有：
  contain：会将图片像是repeat那样填充页面，不会拉伸，当repeat属性为no-repeat时无效；
  cover：不会拉伸或是压缩图片，但是会放大或是缩小以适应背景大小；
  百分比：将图片按百分比方法或是缩小，会自动repeat，不想重复就设置background-repeat属性为no-repeat；
  两个像素值：分别设置图片的宽和高，默认repeat；