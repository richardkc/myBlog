---
title: AJAX相关知识点
date: 2019-08-02 14:02:10
tags:
---
### XMLhttpRequest（简称XHR）
1. 为ajax的核心技术；
2. 主要方法有open()和send()。open("get"（方法）,"example.php"（url）, true（是否异步）);send()中方法为put时，默认无参数或者为null，为post时传输data部分；
3. 同步时：如果接受的是同步响应，则需要将open()方法的第三个参数设置为false，那么send()方法将阻塞直到请求完成。一旦send()返回，仅需要检查XHR对象的status和responseText属性即可；
4. 异步时：如果需要接收的是异步响应，这就需要检测XHR对象的readyState属性，该属性表示请求/响应过程的当前活动阶段。
  4.1 异步时接收的参数值：
          0(UNSENT):未初始化。尚未调用open()方法
          1(OPENED):启动。已经调用open()方法，但尚未调用send()方法
          2(HEADERS_RECEIVED):发送。己经调用send()方法，且接收到头信息
          3(LOADING):接收。已经接收到部分响应主体信息
          4(DONE):完成。已经接收到全部响应数据，而且已经可以在客户端使用了
5. 响应超时：XHR对象的**timeout**属性等于一个整数，表示多少毫秒后，如果请求仍然没有得到结果，就会自动终止。该属性默认等于0，表示没有时间限制
6. 接收到响应后使用request.xxx()即可使用响应内容，一般有以下四种方法：
   6.1 responseText: 作为响应主体被返回的文本(文本形式)
   6.2 responseXML: 如果响应的内容类型是'text/xml'或'application/xml'，这个属性中将保存着响应数据的XML DOM文档(document形式)
   6.3 status: HTTP状态码(数字形式)
   6.4 statusText: HTTP状态说明(文本形式)


### JSONP相关知识点
1. 数据库：能够长久地存放一些数据的地方；
2. 当在html文件中添加form标签提交后台数据时，form表单执行后悔默认刷新页面，可以与iframe标签结合使用使得当前页面不会被默认刷新；
3. 古老的传输数据方法：
3.1 事实上现在用form表单提交数据的前端已经不多了，有一些标签如a、link、script都可以提交数据。
3.2 在script内借用img的方法虽然也可以传输数据，但是缺陷是只能get，无法设置post，且需要将图片输出出来，否则无法执行；
3.3 SRJ(Server rendered javascript)方法：同样的，在script标签内创建一个script元素，而且要将该script元素appendChild为document.body的子元素，然后才可以进行后面的操作。相较于img元素，script元素的方法不用加载图片，运行较快，但是在运行后会动态创建一个script标签，script元素onload时nodejs文件会被执行，如果response.write()之中存在alert，html中也存在alert，会先执行response中的alert；
3.4 JSONP其实就是后台向网页发送的数据对象，我们在callback的时候，只要将.call传输的数据改成一个对象，这个对象里的key必须用 **""** 包裹起来，JSONP其实就是JSON+padding，左右两个{和}分别为左、右padding，中间部分为JSON；
3.5 使用随机函数名后记得将函数名删除，会更简洁；


### JSONP结构
**· JSONP就是通过动态创建script结合callback参数实现的，动态创建的script只能默认用get，无法用post；**
请求方：XXXX.com的前端程序员（浏览器）
响应方：YYYY.com的后端程序员（服务器）
1. 请求方创建 script，src 指向响应方，同时传一个查询参数 ?callbakName=hahaha
2. 响应方根据查询参数callbackName，构造形如
   2.1. hahaha.call(undefined，'你要的数据')  //推荐使用
   2.2. hahaha('你要的数据')
3. 浏览器接收到响应就会执行hahaha.call(undefined,'你要的数据')
4. 那么请求方就知道了他要的数据

约定：
1. callbackName -> callback
2. hahaha -> 随机数  如：var functionName = 'hahaha'+parseInt(radom()*1000,10)

### JSON（全新的一门数据交换语言）与JS的不同之处：
1. JSON没有抄袭JS的function和undefined；
2. JSON的字符串首尾必须是双引号，如{"name":"frank"} {"a","b"};
3. JSON没有变量，因为不是编程语言；没有原型链__proto__；
4. 后台返回的响应第四部分始终是字符串，写出长得像对象的结构只是为了符合JSON的结构语法，便于后面直接用JSON.parse()解析并转换成为JS中的对象；
5. JSON3.js库就是程序员用JS来写JSON.parse()，不用了解;

### AJAX
1. AJAX（Async JavaScript and AML）：异步的JavaScript和XML；
2. 同源策略： 举例：form、a、script等都能向baidu.com发送get请求，但如果页面不是baidu.com里的，就不能向baidu.com发送AJAX请求（此时status为0）；只有协议+域名+端口一模一样才允许发送AJAX请求；
3. 为了避过同源策略，需要使用CORS（跨来源资源共享：Cross-Origin Resource Sharing），即在被请求方后台的响应头添加 **response.setHeader('Access-Control-Allow-Origin','http(s)://xxxx.xxx.com(即填写请求方域名)')** ;
4. 同时cors多个域名白名单不只是单纯地添加逗号，具体的方法去google，需要一段代码确认origin是否为白名单；
5. 当response后台的content-Type设置为text/json时，前端中调用responseText就会默认转换为一个对象，而不是一个字符串；
6. 调用.ajax()会默认返回一个promise值，相当于 **let promise = window.jQuery.ajax()** ;promise自带一个then方法，第一个值默认为success的执行函数，第二个为error的执行函数；