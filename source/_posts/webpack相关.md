---
title: webpack相关
date: 2019-08-25 16:34:09
tags:
---
### 有关sass的使用
1. scss相较于sass是由ruby程序员开发出的一种较为简单的语言，它在语法结构上优于css；
2. scss的使用需要自行安装node-sass，然后通过指令node-sass转换，scss文件不能被html直接引用，需要转换为css文件；
3. 通过git自动转换scss文件为css文件的方法是：在同样的转换指令后面添加 **-w scss文件名**； 
4. 在webpack中使用sass-loader进行转化；

### babel
1. 对于将let转换为var的babel，引用的则是转换后文件夹的文件，而非原本js文件中的文件，如果需要实时转换文件夹中的文件，可以在原转换指令后添加 **-wacth** ；
2. 在webpack中使用babel-loader进行转化；

### autoprefixer
1. 已知flex不适用于部分浏览器和手机系统，所以需要使用autoprefixer进行转化；
2. 实现功能安装的是**postcss-loader**！！！
3. 同时使用sass-loader和postcss-loader时，postcss-loader中的postcss.config.js中的 **parser:'suggarss',** 应该注释掉，不然会出现错误；

### parcel
1. parcel是一种比webpack更加智能的模块打包器，可以自动加载所需的库，还可以自动创建dist等，较webpack更加自动化，便捷；
2. parcel会将打包的scss文件自动转化为随机数名的css文件导入html中，最后得到的文件也可以在dist中找到；

### webpack的bug
1. 指令后面要跟上生产模式！！


**一开始实现代码的自动转换使用的是Grunt，后来使用的Gulp，现在最新使用的是webpack**