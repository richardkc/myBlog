---
title: html小结
date: 2019-04-02 21:33:13
tags:
---
**！！！块级元素和内联元素为css，与html无关！！！**
### 首先是html的基本框架：
· html 5中的< !DOCTYPE html>是最为简洁的版本，前面版本的语句都相当复杂。其中html、head、body等标签都是必加的，这些比较简单就不作详细介绍。
· head、body、footer等结构标签均可以省略，不算语法错误，但浏览器执行时都会默认补上。
· head中的title标签作为网页的“门面”，一般都要加以注释。meta charset="utf-8"作为对字体的编码格式标注，可以不加，但是要确定该网页默认为utf-8编码。
· footer作为页脚标签，可作为全局布局，也可以包含在某一个div标签中，作为某个小块版面的页脚。
· div作为基本的块标签，如果是横向布局，需要用多一个div横排的两个div包含起来；纵向分布则两部分不用包裹起来。div无实际意义，同理还有span标签。div为页面划分，span为横向划分，如我是< span class=name>Richard< /span>，不加class属性，div和span都为无意义划分了。
· class**属性**为多个标签的共有属性，一般加入作为代码识别标注，全称classname。
· h1、h2等为多级标题。
· br为换行，hr为分割线。
· nav全称navigation，作为html 5中的新标签，一般用来将具有导航性质的链接划分在一起，简化结构、便于理解，一般为下拉导航列。
· p标签全称paragraph，一般用来包裹一段文字。
· kbd一全称keyboard，即键盘；一般表示方法例如：< kbd>ctrl< /kbd>+< kbd>c< /kbd>。
· ul为无顺序表格，全称un-odered list；ol为有顺序标签，如第一二名的分布，全称ordered list。
· video为视频链接标签，audio为音频标签。
· small表示不重要，strong表示十分重要，b单纯表示粗体。
· img为图片链接标签。
· dl为描述列表，内含两个标签：dt表示单词，dd表示单词的定义。
· **关于&**，由于&在html中有其他表意，所以在普通文字表述中需要用到&，需表示为“&amp；”。

### iframe标签
· 现在用的较少，但是以前的项目可能会遗留iframe标签。
· 运行原理为新开一个窗口，所以运行时间会很长，会卡顿。
· iframe为嵌套页面、可替换标签，用src连接链接，等于#时为当前页面，frameborder=“0”一般要加，页面会比较好看。
· 用name可与a标签中的target链接，点击a标签可以进行iframe跳转。

### a标签
· target属性中：_ blank 在空页面打开；_ self 在当前页面打开；_ parent 在上一级页面打开；_ top 在最高层页面打开。
· 如果需要下载而不是打开展示，就需要在meta中将content（type）改为application/otcet-stream（默认为text.html），或者在a标签属性中添加download属性，推荐使用第二种方法。
· a标签中不可以没有herf属性，href中可以加锚点和？询问路径，发起get请求。
· href中可以添加伪协议，格式为：“javascript：（代码）；”，执行代码栏。（代码）栏为“#”时页面会滚动。（代码）栏可以为空，点击后不会刷新也不会跳转；或者href中为空，但是页面不跳转会刷新。

### form标签
· 默认重开页面，与a标签一样可以与form标签联用。
· 与a标签发起get请求不同，form标签一般用来发送post请求；但是默认状态为get，所以需要添加method属性，值为post。
· 如果form表单里没有提交按钮就无法提交form，除非用JS；（用input标签，type属性改为submit）。
· input标签中type有username、password等选项，post状态下默认会被提交到第四部分，即form data，get状态下会默认把参数放到查询路径中。post状态下也支持查询路径，需写在action属性的路径后，？后加内容。
· input为button时同样会出现与submit相同的按钮框，但是button按钮默认无法提交；但是特殊情况下，即没有submit时button会自动升级为提交按钮，但此时button中的type属性不能加。
· input中的checkbox为小方格勾选框（多选框），后可添加文字，并用label标签包裹起来进行关联，此时点击文字就可以直接选择勾选框；label不进行把包裹的话需要添加name属性和input中的for属性进行关联；两种做法推荐前一种，比较省事且简洁易懂。input中的name属性一般要加上，不加查询路径中就不会有东西，没有意义，有勾选默认为on状态，可通过修改value属性的值改变，为name=value。
· input中type属性为radio时（单选框），即为可点选圆框，同样通过赋值value可以自主选择返回值，通过赋值同样的name属性可以将radio改为只能单选一个。
· 下拉列表select标签，可以选择不同的内容进行提交，默认为单选，通过添加multiple属性可以改为多选。修改name属性可以定义提交类，通过option标签对value进行赋值可以修改提交数据，value的值可以不填，则由一个空选项；option标签中disable属性为不可选，一般用于满员之类的情况；selection属性为默认选中。

### textarea标签
· 为一个可编辑文本框，通过添加“style="resize:none;”属性用css修改宽高；或者可以直接修改后面的行字数和行数，但两种方法css的较为精准。

### table标签
· 包含三部分：thead、tbody、tfoot；其中都可把包含tr（table row，即一行），tr中包含th（标题）、td（数据），而th和td可以任意排列，可定义竖行为标题，即在每个tr开头添加th，后用td，也可以将第一个tr中全添加为th。
· 通过在table标签中添加border属性，修改其值（1，2等），可以给表加上框；此外，可以将border属性修改为“border-collapse：collapse”语句，就不会出现双线框，较为美观。
· 在table标签中添加colgroup标签，在colgroup标签中添加col标签，通过修改col中width的值修改列的宽度，修改bgcolor的值（如red、green等）改变列的颜色；
· table标签现在使用较少，一般都用css进行设置，了解即可。

杂记：
· 如果想要保全字符串内的换行、缩进、空格等信息，可以用< pre>标签将这部分包裹起来；art