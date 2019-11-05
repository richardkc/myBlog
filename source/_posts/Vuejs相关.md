---
title: Vuejs相关
date: 2019-08-11 15:31:59
tags: vue
---
### axios
1. axois可以说是一个盗版jquery的库，有axios.get/post/put/patch/delete等方法，比jquery.ajax()功能更多，更专注于数据交互；
2. axios优于jquery的还有它可以在数据库返回response前自己拦截数据，axios.interceptors.response.use(function(){})方法会接收一个函数，并设置response.xxx等属性，返回；

**在ajax方面，可以用axios；在普通api则可以用vue，所以可以说jquery往后就可以省略了**

### Vue与MVC
1. Vue用来替换MVC中的view，vue中的template只能有一个根元素，多的不显示；
2. Vue中如果觉得controller中的赋值太过繁琐，可以将view中data中的数据再用一个对象包起来，后面赋值如：this.view.xxx = this.model.data即可；
3. Vue的优点在于能局部刷新，传统方法基本都是需要全部刷新的；
4. Vue使用method方法将controller取代了，只需要在元素属性上加相应操作即可触发method中相应函数；
5. Vue能实现内存和页面的双向渲染；

### Vue的基础属性
1. v-bind：绑定；通过绑定html元素，可在js中新vue的data中获取其值；
2. v-if：条件；同样从data中获取，当值为true时显示，为false时不显示；
3. v-for：
4. v-model：
5. v-on：

### Vue进一步加深

### vue的额外笔记
1. v-cloak：该属性一般用来标记特定的元素，在页面没有缓存并加载时起作用，设置元素在css中为 display:none ，js加载时会自动删除html元素中的v-cloak属性，使得元素正常运行；该元素作用是防止页面刷新时出现额外错乱；(本人在项目实践时发现v-cloak有时候会出现bug，这时候需要给设定部分包裹上一个div再给这个div设置v-cloak即可)
2. $event为vue的事件对象，里面存储着事件相关属性；在本人vue-resume的demo中，$event就可以用来传递实时编辑的文本；
3. 实例的文件必须在组件后面啊！！