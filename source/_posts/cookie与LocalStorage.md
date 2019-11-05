---
title: cookie零散知识点
date: 2019-08-21 23:01:55
tags:
---
### Cookie： （4KB）
1. 服务器通过 Set-Cookie 头给客户端一串字符串；
2. 客户端每次访问相同域名的网页时，必须带上这段字符串；
3. 客户端要在一段时间内保存这个Cookie；
4. cookie默认会在用户关闭页面后就失效，但是后台代码可以设置cookie的过期时间；
5. cookie也是存储在c盘的，但是每次请求都会被带到浏览器上；
6. 前端不要去读写cookie！！
7. window.navigator.cookieEnabled;验证浏览器是否开启cookie功能；
8. document.cookie查询当前网页的cookie；

### Session：
1. 将 SessionID （随机数）通过Cookie发送给客户端；
2. 客户端访问服务器时，服务器读取 SessionID；
3. 服务器有一块内存（哈希表）保存了所有 session；
4. 通过 SessionID 可以得到对应用户的隐私信息，如 id，email等；
5. 这块内存（哈希表）就是服务器上的所有 session；
6. 大部分情况下依赖cookie，但是也可以不依赖cookie；

### LocalStorage
1. localStorage.setItem(name,id)：接收name和id，并将两者转换为字符串存入哈希；
2. localStorage.getItem(name)：接收name，从哈希中获取相应的id；
3. LocalStorage.clear()：清空栈；
4. LocalStorage事实上是存在c盘文件中的;
5. localStorage与http无关；
6. HTTP不会带上LocalStorage的值；
7. 只有相同域名的页面才能相互读取LocalStorage（但是没有同源那么严格）；
8. 每个域名loc最大存储量为5MB左右（不同浏览器不一样）；
9. 常用场景：用来记录有没有提示过用户（除密码等隐秘信息外）；
10. 理论上永远存在，除非用户手动修改（快捷键ctrol+shift+delete）；

### SessionStorage（会话存储）：和LocalStorage功能相同，但是会在用户关闭网页后过期；

### 杂记：
1. chrome会自动屏蔽response hearders中的Set-Cookie，要查看可以从网址的按钮查看；
2. 后台在替换html中的特殊字符段时要注意添加string =，不能单写string.replace()方法；
3. 网页在application中如果没有阻止可以轻易修改cookie的值并获取信息，所以就需要session的使用；