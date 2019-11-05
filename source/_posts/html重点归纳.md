---
title: html重点归纳
date: 2019-09-03 15:36:43
tags:
---
### <DOCTYPE>（document type）
1. 呈现模式：标准模式：< !DOCTYPE html>；混杂模式：< !DOCTYPE html>不存在或错误；

2. 标准模式作用：按照W3C标准渲染页面；

3. 混杂模式作用：较为宽松，兼容一些老节点；


### table
1. 包含三部分：thead、tbody、tfoot；

2. 三部分都可包含tr（table row，即一行），tr中包含th（标题）、td（数据），而th和td可以任意排列，可定义竖行为标题，即在每个tr开头添加th，后用td，也可以将第一个tr中全添加为th。

3. table标签现在的使用变少了，考虑使用其他方式；

### form
**表示了文档中的一个区域，此区域包含有交互控制元件，用来向 Web 服务器提交信息**
1. 