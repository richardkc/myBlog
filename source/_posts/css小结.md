---
title: css小结
date: 2019-04-18 20:05:23
tags: css3
---
### css杂述
·全称“层叠样式表（Cascading Style Sheets）”，现学版本为css3。
·周边工具有LESS CSS（功能更多，更为简洁的CSS语言）；SASS（同LESS CSS）；PostCSS（一种CSS处理程序）。

### css学习资源
·一般标签及其使用功能检索推荐使用Google搜索：关键词+MDN；
·CSS Tricks中有各种有趣实用的技巧；搜CSS trick shape首个网页可以获取各种小图形的代码；
·中文博客参考推荐阮一峰和张鑫旭的；
·Codrops中有各种炫酷的CSS效果；
·CSS 2.1的中文spec（由于中文翻译较慢，建议参考英文）；

### css的四种链接方式：
1.html中内联 style 属性，在style标签内使用 @import url() 也可以引入外部文件；
2.html中在 head 标签中添加 style 标签；
3.链接外部文件css， head 中使用 link 标签；
4.css文件中链接css文件： @import url(./xxx.css)； 。

### css杂碎知识点汇集
·block块级元素有另起一行的特点。
·一个元素一般有margin（外部的宽度）、border（边框）、padding（内部的宽度）。
·居中：text-align: center; 。
·对于backgrond-color属性和background属性，前者范围较小，只能定义背景色；后者能设置背景颜色，背景图片、定位等。
·float属性有left和right两个，使用float浮动要在父级元素的class属性中添加clearfix，clearfix书写在css文件中，具体为：
.clearfix::after{
    content: '';
    display: block;
    clear: both;
}
·消除ul、ol等列表固有的属性，只需添加list-style： none。

·消除a标签自带的下划线，只需添加text-decoration： none。

·有关字体的属性，font-size为字体大小，font-family为字体选择，font-weight调节字体粗细。

·hover伪类为鼠标上置时的效果。

·在添加鼠标上置效果时为防止外边框的移动，一般先在原标签添加一个透明的边框，再在hover伪类中添加一个有颜色的边框。

·将内联元素变成块级元素，可以添加边框，只需添加display：block；。

·同理添加display: inline；可以将块级元素变成内联元素。题外话，一般使用display： inline-block用以改变块级元素换行特性，会带有很多bug，导致内容不居中，需要居中需添加ververtical-align：top属性，所以不推荐使用，一般使用float更加安全，但是inline-block属性值的应用还是很广泛的。

·color之类的属性继承父级元素的属性只需将子元素的属性值改为inherit。

·**body默认会有一个margin，大小为8px**，消除掉只需将其margin的值改为0。

·块级元素（如div）的高度由其内部**文档流元素**的高度总和决定。

·文档流：文档内元素的流动。

·内联元素如果遇到页面宽度不够，就会往下一行流动，其中中文可以逐字流动，而英文的一个单词不会拆分在两行；如果要强制将英文单词换行，需要给其添加word-break： break-all；（keep-all为全不要打断）；此外块级元素不会流动。

·line-height属性设置行高，如1.5设置为原基础的1.5倍，50px设置为行高50px。

·vertical-align属性用来设置元素的垂直对齐方式，一般用来对齐父级元素，默认值为baseline。

·background-image：url（）用来插入背景图，一般会给出height，但是不是不得已不要添加，height和width会出很多bug。

·position： fixed；是脱离文档流，使元素相对于页面定位。一般还要附加left： 0；top: 0；用于消除边距。

·使用width： 100%；继承父级元素属性时，子元素如果有左右padding之类的会造成bug，处理方法是将左右的padding改为0，上下保留；然后在原基础的div上再嵌套一个div，给上级的这个div添加padding就可以达到目的了。

·color属性中值为rgba（）时括号内最后一个值为透明度，范围0-1。

·background的background-position：为位置设置，当两个值均为center时，元素居中。

·background的background-size：为大小调节，当其值为cover时，元素自动覆盖，还会自动适应网页界面的收缩。

·一般使用width会出现bug，但是可以通过设置max-width：属性来调节最大宽度，而且页面收缩时会自适应，但是页面放大最大适应也只能达到max-width的值。

·使一个元素快速水平居中可以使用margin-left： auto；margin-right： auto；属性。

·调节img标签图片的大小可以直接在html文件标签中添加width、height属性进行调节，不用另写css。

·span标签的样式重构不推荐使用width、height直接修改，可以将元素的display属性改为inline-block值，然后通过设置padding和line-height属性进行调节。

·**关于使用div画简易图形的**，一般通过调节div的border属性的上下左右颜色、宽度进行裁剪，最后将想要部分的border颜色修改为目标颜色，其他border颜色统一修改为transparent（透明），就可以获取特殊图形块。

·由于span中不能添加div，所以添加一个span将其display： block；即可。

·**要想将两个元素相对定位，需要在父级元素中添加position： relative；在子元素中添加position： absolute；不添加系统不会自动识别父级元素与子元素之间的定位信息**。

·将两个span图形块合并在一起，可调节子元素的top、left之类属性，通过设置top： 100%；使上下父子元素拼合。

·当添加了max-width属性，再添加padding就会改变整个div的大小，所以需要在原div中再添加一个过渡的div包裹原来所有元素，并给子div添加padding就可以解决问题，**在很多位置信息有冲突出现bug时大部分可以通过嵌套div解决**。

·去掉所有元素自带的margin和padding属性值时可用*号代指所有元素。

·元素float后可通过调节width的百分比分配行的宽度。

·引用图标可以使用阿里的'www.iconfont.cn'，将图标添加到购物车后新建项目，生成代码后按照帮助中的说明用symbol方式引用。在head中插入script标签，并将帮助的第一部分代码插入head中，随后将svg插入到使用区域。通过给定width和height设置大小，**切记改变颜色要用fill属性！！不是color！****调节图标下面有边距的问题，引用vertical-align：top；即可。一般加了inline-block都要加vertical-align：top；，才不会出现下半部分有空隙的情况。

·画圆可以用border-radius属性，圆角同理，标准圆50%，画圆角一般几个px就够了。

·关于空元素，div、span之类中间能添加内容的都不是空标签，input之类的没有结束标签的都是空标签。

·**所有非空标签都有伪类！**div标签的before和after伪元素，一般不会显示，可以通过定义div的前后两个伪类给所有的div加上边框之类的东西，加上的内容不能被选中，而且不能被复制。

·使用before和after伪类必须给content，值可以为空，但是必须加，而且必须display：block；。此外，伪类内不能再加伪类了。

·画图时需要渐变可以google css 3 linear gradient查找辅助工具，调解后复制代码即可。

·关于**CSS动画**，参考可以Google css animation，原标签的css中必须引用animation-name和animation-duration（周期）。

·margin的值可以为负值，一般用来推动元素覆盖。

·对于内联元素的居中，无法直接用margin：auto；所以需要给其添加一个父级元素，给父级元素添加text-align：center；。

·阴影效果可以google css shadow generate，调节后复制调用代码。

·对于技能条类的div矩形条空隔，使用内嵌div的方法会出现后半部太长的bug，推荐使用box-sizing属性，添加box-sizing：border-box；后通过设置padding即可，此时的padding将会自动加在width的百分比中。

·伪类nth-child（）可以用来选中特定的子元素，值一般为序号，也可以统用even、odd等批量选中。其中nth可以为序数词（first、second...）此时即可省略后面的括号及内容。

**一般标签后加单个：的为伪类，有两个：的，如：：after为伪元素。**
·关于鼠标点击移动的特效，以ol为例，首先要给每个li和移动矩形div各一个特定的id，矩形div中还需给class增加state-1以保持页面加载时是state-1的情况，然后在后面添加script标签，标签内使用xxx。onclick= function（）{}函数，在函数内添加属性xxx。className = 'xxx2 state-1'；。以此类推添加state-n即可，在css文件中对每种state-n情况进行设置。**此外，如需设置动画运动时间，在矩形div中的上级div设置transition：all（声明所有对象）？s；即可。

·margin在IE浏览器有bug。

**找免费的psd文件可以直接Google webpage free psd。**

### CSS杂记（实践）
1. 如果有两个或以上div嵌套时，如果其中一个子div的display定为flex，这个时候修改其父级元素的width会给其和其子元素的width造成干扰，解决方法是讲其父级元素同样修改为flex属性；
