---
title: 实践遇到的bug
date: 2019-09-24 18:15:14
tags:
---
1. contenteditable=true不获取其target中innerText时输入正常，但获取使用其值后就会出现一系列bug，比如光标乱跑，换行时错乱等，不同浏览器的bug表现也会有所不同；