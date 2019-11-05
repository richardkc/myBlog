---
title: jQuery知识点
date: 2019-07-21 20:30:20
tags:
---
## JQuery相关知识点
#### 中文版的jQuery API文档登陆 cndevdocs.com   jQuery的官网是 https://www.jquery123.com/
1. this是call的第一个参数；

2. instanceof：用于测试构造函数的prototype属性是否出现在对象的原型链中的任何位置，如 **XXX instanceo f Node**；

3. 引用jQuery：
3.1 cdn引入 ：< script src="https://cdn.bootcss.com/jquery/3.4.1/core.js"> < /script>（搜cnd.js，输入jquery）； 
3.2 本地引入：< script src='js/jquery/jquery-1.11.3.min.js'>< /script>；

4. API：
4.1 addClass、removeClass(className)：不接受数组，只接受className，给选中节点添加新的className/删除旧的；**链式操作：.addClass和.removeClass可以连用在一行，不用换行重写节点名**s
4.2 toggleClass(className)：切换选中节点的class中特定的className，如果没有就添加该className，有就删除该className，以达到切换效果；
4.3 addClass、removeClass(function(index,currentClass){})：function中的两个变量名是默认不变的，通过var一个classes数组，将每个节点所要添加的className按顺序添加到数组中，通过调用classes[ index]，就可以在当前操作节点数组中按顺序添加新的className/删除旧的；
4.4 jQuery除了DOM API，还有动画、AJAX等模块；
4.5 **window.$ = jQuery，所以引用jQuery时可以直接  var XXX = $()  ，此处的$直接等同于jQuery，还有一个默认的习俗，就是使用了jQuery的对象前面加$作为标记，以免混淆其他DOM API，如  var $XXX = $()  ;**
4.6 了解javascript source map可以搜阮一峰的教程；
4.7 .eq()方法：找出对应的DOM，并把其封装成一个jquery对象；
4.8 .trigger()：据绑定到匹配元素的给定的事件类型执行所有的处理程序和行为，括号内可以用来触发click、touch等事件。
4.9 .one()：执行一次操作，并在执行后删除相关操作，jquery中能将function替换成flase，此flase在语句中能阻止默认传播（冒泡和捕获）和默认操作；
4.10 .hide()：不接受参数，能隐藏当前元素；
4.11 .show()：与hide相反，能显示当前元素；
4.12 .offset()：在匹配的元素集合中，获取的第一个元素的当前坐标，坐标相对于文档。 设置匹配的元素集合中每一个元素的坐标， 坐标相对于文档。与hide方法连用后使用show方法是无缝轮播的一个关键；
4.13 .remove()：将匹配的元素从DOM中删除；
4.14 .each()方法功能与DOM中的forEach相似，但是传参顺序相反，each的是(index,ele)，forEach的是(ele,index)；
4.15 .animate()方法可以接受三个参数，第一个是css文本内容，用{}括起来，表示动画结束的状态，第二个是动画持续时间，单位为ms，第三个为回调函数，在动画结束后执行；
**轮播组件可以上idangero.us查看；**

5. **html引用jquery需要注意！！**
5.1 外部文件引用时需要将jQuery的script放在外部js文件的链接前面；
5.2 一般把js文件的script标签放在head中，系统会在document加载前就运行，这样会导致许多API无法识别，一般放在body的最后就不会有问题；
5.3 如果一定要把js链接放在head中那就需要在外部js文件中调用jquery的.ready方法，具体操作为：$(document).ready(function(){//这里放你要运行的函数});这样就可以在document加载完毕后再运行js文件；
5.4 不调用外部js文件的话，直接将jquery的链接放在head中即可，body中直接在script标签中正常书写，不过也要放在body的最后部分；

6. jquery杂记：
6.1 用$()包裹一个普通对象可以将其变成一个jquery对象；用${}包裹代码段可以将代码段内部进行jquery运算，一般用在.css()方法中对jquery参数引用；