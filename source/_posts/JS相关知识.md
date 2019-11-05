---
title: JS相关知识
date: 2019-07-17 13:18:37
tags:
---
## JS相关要点
### 1. 标准库
1.1 JS内存中有两种存储方式：堆（heap）和栈（stack），栈中有个变量global（浏览器中为window），其分为标准库和非标准库，标准库又分为object、string、number、boolean等函数；
1.2 object不new直接给对象，就会直接创建一个对应的对象，如Object(1)创建一个Number对象；
1.3 string、number、boolean等不加new返回的就是一个相应的类型数值，前面加new，如new String，就是创建一个新的数组对象；
1.4 boolean的五个falsy值：0、NaN、''、null、undefined；
1.6 array作为用于构造数组的全局变量，不用new或者使用new结果都是一样的，此外Array[2]表示定义一个长度为2的空数组，Array[2,2,2]定义一个长度为3，内容均为2的数组；
1.7 函数function不使用new就是普通的定义法，当使用new function时，内容要填为var f = Function('a','b','return a+b')的格式，注意此处的Function开头为大写，其性质是全局对象；


### 2. 数组Array和伪数组argument
2.1 伪数组相对于数组在push等功能上缺失，伪数组直接连接object.prototype，与array.prototype没有关系。但是key都是一样0、1、2...顺序排序的；
2.2 array的API：
    forEach：格式为  **数组.forEach(function(变量一，变量二){})**  （变量正常情况下为两个）。当function中变量个数为三个时，除了传输value、key，还会在传输一个数组；
    sort（快速排序函数）：格式还是  **数组.sort(function(变量一，变量二){})**  。括号内的两个变量用来定义数组的大小排序方向，当return的值为 变量一-变量二 时，为从小到大排序，变量二-变量一 时，为从大到小排序；还可以通过使用hash辅助排序，当需要排序一个没有具体数值（如名字）的数值，可建立一个新的hash，以名字为key，数值为value，然后使用  **数组.sort(function(变量一，变量二){hash(变量一/二)-hash(变量二/一)})**  得到具体排序；
    join：间插函数，如令a=[1,2,3]  a.join('啊')可输出一个字符串"1啊2啊3"，不传参数时默认用','分隔，也是数组变成字符串的函数；
    concat：连接函数，如令a=[1,2] b=[3,4]，使用a.concat(b)即可返回一个新的数组为[1,2,3,4]。当其中一个为空数组时，可以复制一个全新内存的数组，即两个数组绝对不相等（一般==操作时两个数组是完全相等的）；
    map：映射函数，和forEach功能几乎一致，不一样的点是forEach没有返回值，而map有返回值，且会将引用函数的操作结果收集起来形成一个新的数组；配合箭头函数（=>）使用更方便，格式为  **数组.map(value=>value*2)**  ； 
    filter：过滤函数，与map相似，可以通过限制条件返回特定范围值的数组，如最后 return value>3 ，最后得到的数组就会将小于3的value过滤掉，剩下的value存储为一个新的数组；
    reduce：遍历运算函数，格式如  **数组.reduce((sum,n) => sum+n)**  最后就会返回一个经过算法运算的**值**。功能最强大，可取代map、filter等API的功能，只需要将例子中的sum替换成函数，n替换为空数组[]，在函数内输入操作过程即可；
    **（不同的API可以一起使用，格式如  数组.filter().map()  最后就会返回一个经过筛选并数值运算的数组）**


### 3. 函数
3.1 函数function可以说是变量的一种特例，当x为函数时，调用console.log(x)时，如果x不能直接打印出来，就会自动调用.toString函数；
3.2 对于匿名函数，必须赋值给另外一个变量，**具名函数也可以赋值给变量**。当具名函数赋值给一个变量后，console.log()就不能直接使用函数名打印，原因是此时函数名只能作用在函数域中（普通定义的函数名可以作用在全局）；
3.3 对于window.Function函数对象，假如n=1，对于  **f = new Function('x','y','return x+'+n+'+y')**  ，f(1,2)输出的值为4，要特别注意；
3.4 **箭头函数**，格式为  **f=(x,y,z)=>{ return x+y+z }**  ,执行语句只有一句时，格式可以为  **f=(x,y,z) => x+y+z**  ，变量只有一个时同理，可以将括号省略；
3.5 function的name属性，格式为 **函数/变量名.name**  一般具名函数的name为其名字，被赋值匿名函数的变量的name为变量名，被赋值具名函数的变量的name为原具名函数名，new Function赋值的变量的name为“anonymous（匿名）”；
3.6 若f为已定义函数，调用f时会被当做对象，输出函数体；而f.call()是指执行该对象的函数体；
3.7 函数基本有name、params（参数）、fbody（函数体）等主要部分；
3.8 与array一样，函数也拥有自己的function.prototype，在其中包括了函数体等部分；
3.9 两种调用方法： **f(1,2)和f.call(undefined,1,2)**  ，后者才是真正的调用，建议使用后者；
3.10 在f.call(undefined,1,2)中，undefined就是this，[1,2]就是argument，普通的f(1,2)中就只有argument；
3.11 严格模式：在函数体内加  **'use strict'**  ，进入严格模式后，调用函数，函数的this就不再是undefined默认转换为window，而是保留原来的undefined；
3.12 函数递归等操作时遇到stack flow的问题或者别的bug都直接google‘stack flow’，进入里面查询。
3.13 关于函数作用域，通常见到的说不加var，直接写‘a=xxx’就是在声明全局变量是不对的，函数内使用会被首先理解为赋值，当全局范围没有声明a，那么这个时候函数内的‘a=xxx’就是在给全局变量声明并赋值；
3.14 函数作用域的三个易混淆问题：
**① ————函数作用域内要特别注意变量提升的问题！变量提升但是赋值并不会被一起提升！看到代码要习惯先变量提升！！**
**② ————函数作用域内嵌套函数，在调用嵌套函数f2时，被嵌套函数f1作用域内的变量值是不会影响到嵌套函数f2的，如果嵌套函数f2内没有定义该变量，那使用时就会直接调用全局变量的值**
**③ ————代码执行后再操作（如onclick），变量的值不一定就是当前click的第几个数。举例使用for()循环，再在函数域内定义onclick，当用户onclick时，输出的变量将会是for循环结束的最后一个数，因为此时onclick函数内并没有定义i，打印出来的i将会是此时全局变量中的i，而for循环代码执行并结束后的i已经是最后一个i了，全局变量的i已经被重新复制。**
3.15 闭包：如果一个函数使用了其范围外的变量，那么（此函数+此变量）构成的整体就叫做闭包；
**————eval函数：给一段字符串，把其当作代码执行，格式为 eval('字符串') ————**


### 4. DOM API（DOM全称：Document Object Model）
#### Node接口属性
4.1 JS中的对象都是继承自object，而页面的对象是继承自node，此处的node跟node.js没有关系；
4.2 在html中，html标签的nodeType为document，一般元素为element，文本为text，（注释为comment ……），这几种都归属于node，一开始DOM是设计给XML用的，所以在html中会出现很多问题；
4.3 childNodes：查询子节点，在node中，换行会被充当为一个文本，查询document.body.childNodes时会出现多余的text；
4.4 children：获取子标签，但是**不会获取text**；
4.5 lastChild、firstChild：获取最后一个节点/获取第一个节点；
4.6 firstElementChild：获取第一个非text节点；
4.7 previousSibling、nextSibling：获取上一个/下一个节点（包括回车构成的节点）；
4.8 previousElementSibling、nextElementSibling：获取上一个/下一个非text节点；
4.9 nodeName：获取节点名称，一般如 **ducument.body.nodeName** ，获取的都是BODY这样的大写名称，特殊的如document，直接获取会输出"#document"，要获取真正的name（HTML）需要使用 **document.documentElement.nodeName** ；如svg标签获取的名字是小写的svg，有且仅有这一个，原因是svg是后添加的；
4.10 nodeType：获取节点的类型，一般会用数字输出类型，不会输出一串字符，这样使用是因为以前的计算机内存不够大，常用的如**1代表元素element，3代表text，7代表用于XML的ProcessingInstruction（声明），8代表注释comment，9代表document（即html节点），10代表DOCTYPE，代表DocumentFragment节点（Docment的API唯一有价值的考点）；**
4.11 nodeValue：返回或设置当前节点的值（包括text中的文本）；
4.12 outerText：非标准，尽量不要使用；
4.13 ownerDocument：用来查看节点所属的document，一般页面只有一个document，但是如果使用了iframe标签就会有两个document，所以可以用此API进行验证区分；
4.14 parentElement、parentNode：寻找父级元素/节点，功能相似；前者当父节点不是DOM元素时返回null；后者当节点类型为Attr, Document, DocumentFragment, Entity, Notation时，返回null；
4.15 textContent(firefox)、innerText(IE)：都是获取文本内容，但是有些区别。前者会获取元素所有内容，但后者不会获取元素中的< script>和< style>的值；后者会意识到样式，不会返回隐藏元素的值，前者会；在小于等于IE11版本的IE浏览器中，后者不仅会移除当前元素的子节点，还会永久性地破坏所有后代文本节点；

####Node接口方法
4.16 appendchild()： 将一个指定节点添加到指定父节点的子节点列表末尾；
4.17 cloneNode()：复制节点，括号内为true时，执行深拷贝，括号内为flase时，执行浅拷贝；
4.18 contains()：询问当前节点是否包含括号内节点，返回值为boolean；
4.19 hasChildNodes()：询问当前节点是否有子节点，返回布尔值；
4.20 insertBefore()：在参考节点之前插入一个拥有指定父节点的子节点；
4.21 isEqualNode()：判断两个节点在形式外形上是否一致，返回布尔值；
4.22 isSameNode()：判断两个节点是否严格相等，可以理解为两个节点是否为同一个，同样返回布尔值；
4.23 removeChild()：移除括号内的一个子节点，返回被移除的子节点，可以用 let+变量 接收被移除节点，被移除的节点并不会从内存中消失；
4.24 replaceChild()：语法：**replacedNode = parentNode.replaceChild(newChild, oldChild);**，如果该节点已经存在于DOM树中，则它会被从原始位置删除；
4.25 normalize()：常规化，将当前节点和它的后代节点”规范化“（normalized）。在一个"规范化"后的DOM树中，不存在一个空的文本节点，或者两个相邻的文本节点。具体例子见mdn；


### 5. Document接口
###属性
**只有document才有document接口，也就是该接口专为document准备**
5.1 anchor：已弃用；
5.2 body：获取body元素；
5.3 characterSet：获取字符编码格式；
5.4 childElementCount：获取子标签的数量；**（html元素虽然是根元素，但是其实document在设置里是高于它一级的，是其父级元素）**
5.5 children：获取其子元素；
5.6 doctype：获取doctype内容；
5.7 documentElement：返回文档对象的根元素（HTML）的只读属性；
5.8 domain：获取域名；
5.9 head：获取head元素；
5.10 fullscreen：控制浏览器，使得一个元素与其子元素，如果存在的话，可以占据整个屏幕，并在此期间，从屏幕上隐藏所有的浏览器用户界面以及其他应用。document中对应的退出使用exitFullscreen方法；
5.11 hidden：查询文档是否被隐藏，返回布尔值；
5.12 images：获取页面中所有的images标签；
5.13 links：获取页面中所有的link标签；
5.14 location：是一个只读对象，返回一个location对象；包含有文档的 URL 相关的信息，并提供了改变该 URL 和加载其他 URL 的方法；
5.15 onXXXXX：监听系列，如onclick、conmouseend、onmouseleave等；
5.16 origin：返回只读属性的文档来源；
5.17 plugins：查询插件；
5.18 readyState：查询文档是否加载完毕；
5.19 referer: 引荐者，返回引荐请求页面的域名；可以通过referer禁止引用图层等元素；
5.20 script：获取script标签；
5.21 scrollingElement：获取正在滚动的元素；
5.22 styleSheets：获取所有的css；
5.23 title：获取页面的title；
5.24 visibilityState：查询页面是否被显示，返回布尔值。一般页面正在被查看返回的都是true，页面处于闲置状态获取的都是false；

###方法
5.25 open()、write()、close()：打开文档；书写文档，内容写在括号内；关闭文档；**document的书写有三个步骤：open、write、close，一般连着的write写入后就会关闭，下一次调用write就会重新open，并覆盖掉document的原内容，容易造成文档内容丢失，不建议使用**
5.26 createDocumentFragment：创建一个新的空白的文档片段；
5.27 createElement()：创建一个新元素；
5.28 createNode()：创建一个新的文本节点；
5.29 execCommand()：一般用于写自己的**富文本**编辑器，可以控制颜色、粗细、复制文本等，但是使用前要检查浏览器是否支持，使用有一定风险；
5.30 exitFillscreen()：退出全屏；
5.31 getElementById()：通过id获取元素；
5.32 getElementByClassName()：通过class获取元素；
5.33 getElementByName()：通过name属性获取元素；
5.34 getElementByTagName()：通过标签名获取元素；
5.35 getSelection()：获取用户选中的文本；
5.36 hasFocus()：返回一个 Boolean，表明当前文档或者当前文档内的节点是否获得了焦点。该方法可以用来判断当前文档中的活动元素是否获得了焦点；
5.37 querySelector()、querySelectorAll()：都是选择器，但是前者只会返回选中的**第一个元素**，后者会全部返回，且返回的classlist是一个**伪数组**，**（DOM API获取的elements都是伪数组，与前面的arguments相同）**；
5.38 writeln()：与write不同的是此方法只会写一行；


### 6. Element接口：
###属性：
6.1 attribute()：获取一个元素的所有属性；
6.2 clientHeight()、clientLeft()、clientTop()、clientWidth()：**都是只读属性，单位都是像素**，获取元素内部高度 ； 元素的左边框宽度，不包括左外边距和左内边距 ； 元素顶部边框的宽度，不包括顶部外边距或内边距 ； 元素的内部宽度，包括内边距，但不包括垂直滚动条（如果有）、边框和外边距；
6.3 firstElementChild()：获取元素第一个子元素；
6.4： innerHTML()：功能与innerText相似，但是可以通过添加标签来给文本添加样式等操作，这样做也会有风险，操作者可以通过这样的操作使用script，console.log出页面的document.cookie（谷歌浏览器通过iframe阻止了这种操作，但是IE bug比较多；

###方法：
6.5 element也可以操作querySelector、querySelectorAll方法，就是说可以直接div.querySelector()，不一定非得用document；
6.6 MDN中海油移除一个属性，设置一个属性等更多操作，了解更多去看MDN；


### 7. DOM事件：
7.1 DOM Level 1可以说是将DOM Level0的东西汇总起来；
7.2 目前用得最广泛的标准是DOM Level 2；
7.3 **DOM Level 2中监听事件普通模型与队列模型用法的不同：**
7.3.1 普通模型，如.onclick()事件，但是监听事件只能执行最后一次的监听，也就是说如果有两个或以上的同样的监听事件，前面的监听事件会被覆盖，所以一般不推荐使用；
7.3.2 队列模型，如.addEventListener('click',function(){}，undefined)。当有多个元素同时调用.addEventListener()方法，且这些元素之间存在父子级关系时，存在这些关系：undefined的值为false时，执行顺序是从最小级到最大级（冒泡阶段）；当undefined值为true时，执行顺序从最大级到最小级（捕获阶段）；当一个节点上面同时存在捕获和冒泡阶段时，执行顺序就看是谁先被写出来；
7.4 .stopPropagation()方法可以阻止冒泡或捕获的询问传递，在Chrome和Firefox上都没有bug，但是在IE8中与checkbox结合时会出现bug，checkbox不能被点击；
7.5 document.addEventListener(visibilitychange,function())方法可以监测页面是否正在被观看，由document.hidden做出判断并执行代码；


### 8. leancloud（leancloud.cn）
8.1 主界面创建一个应用；
8.1.1 引入一个 av-min.js，得到window.AV；
8.1.2 初始化AV对象（直接拷贝官网代码）；
8.1.3 新建一条数据（同样直接拷代码）；
8.2 监听用户提交事件时应该监听form的submit，而不是监听input，此时支持点击按钮或回车提交；


### 9. 杂记
9.1 DOM的最小组成单位是节点Node；
9.2 节点的七种类型：Document、DocumentType、Element、Attribute、Text、comment、DocumentFragment；
9.3 全局变量不可用，window下的所有属性名都不能用作各种名称。
    局部作用域内变量名跟全局属性名重复就不会出现bug，比如声明一个函数并在内部var一个parent，这里的parent就不会跟外部的全局属性名冲突。
    或者可以使用**函数立即调用法**，如function(){}.call() / function(){}()立即调用，这样也不会跟全局变量重复。但是由于这个方法浏览器不识别，所以需要多加东西来使浏览器识别，如直接括号整个部分、括号function(){}、在function前面加-号或+号或！号或~号。这些方法是让浏览器知道前面不是在定义函数，而是在定义一个值。这些方法都是以前的方法，升级后js使用了{}代码块，如{let parent = 1}；
9.4 setTimeout()和setInterval()方法的区别在于，前者是在延迟结束后执行代码段；后者是在每间隔延迟时间后执行一次代码段，多次执行；
9.5 浮层点击事件的阻止有两个方法，第一个是使用stopPropagation()方法阻止button的触发事件冒泡上传；第二个是使用setTimeout()并时间置0的方法将document的click事件延迟执行，直到下一次click事件再次执行；
9.6 在用swiper copy别人代码时，要查看github的lisence许可状况，可以搜 **阮一峰 lisence** 查看，MIT lisence是最开放的代码。
9.7 由于浏览器的优化特性，当窗口被闲置或切换，setTimeout和setInterval方法会停止运行，IE没有这个问题，但是IE也比较占内存；
9.8 ES6中赋值方式进一步优化，其中解构赋值可为： **let {method,body,successFn,failFn,headers} = options** ；
9.9 tween缓动函数是调节速度与时间关系的，有自己的库，可到cdnjs中搜查，引入后再引入其例子,例子通过google tweenjs便可获取；
9.10 立即执行函数：为了不使某个变量变成全局变量，需要用function(){}.call()将函数装载并调用，但是ES6已经不支持这种语法了，所以需要写成 !function(){}.call() 这种方法会改变函数返回值，使其取反；或者写成 (function(){}.call()) ，但是这种方法不能再在前面添加东西，不然很容易使浏览器产生误解；还有就是可以写成 随机数.call() 的形式，但是写法又复杂了些，而且还是有冲突的可能的，虽然很小；一般推荐使用第一种；
9.11 promise方法：对于一个执行的函数，在后面加上.then()方法，就能实现promise结构，then中数据为(success:f1,fail:f2)，即成功就执行第一个函数，失败执行第二个函数。如果在then后面再加then，第二个then中的success部分就是当第一个then中两个函数都能正确执行时执行，只要第一个then中有一个函数不被执行就会调用fail部分的函数。
9.12 有关**this**，this永远是call()的一个个传参，在触发事件xxx.onclick中，this代表的是触发事件的元素，在xxx.addEventListener中，this代表的是该元素的引用xxx，在jquery语法中，this又代表与selector相匹配的元素，如 **$('ul').on('click','li',function(){})** 中，this代表的是li；不同的事件中this的指向始终不同，所以不确定的情况下需要查阅相应的文档；
9.13 有关**new**，由于对象的共有属性和自有属性需要封装和相互调用，所以自有属性函数内需要创建临时对象和引用共有属性，还要返回一个对象，步骤很繁琐，所以就有了new，js中只要在调用自有属性函数时，js就会帮你完成默认步骤，你只需要在自有属性函数中直接写上自有属性定义，在共有属性对象中直接添加共有属性，必须注意的一点是**共有属性名=自有属性名.prototype**，这样js就会自动识别；
9.14 有关下载jquery库无法使用的情况，是因为git会将其提交，所以需要将下载的jquery文件（node_modules）放入一个内部文件夹再引用，这样jquery可使用（强制添加指令：git add -f）。
9.15 有关**setInterval**方法，事实上，setInterval方法读取第一个值之后，就只会执行第一个值的代码，后面改动也不会变化，所以就需要用setTimeout来模拟setInterval的功能，就是给setTimeout的函数参数function命名（如fn），在setTimeout内判断条件后延时调用setTimeout(fn,时间间隔)，这样在规定条件下就会循环执行，而且不用clear，还能修改时间间隔。