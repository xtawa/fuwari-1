---
title: 记一次电子班牌破解记录
published: 2025-07-10
description: '本篇文章详细写出了作者在破解基于安卓系统的电子班牌的操作记录与灵感启发等内容'
image: ''
tags: [破解,记录]
category: '记录'
draft: false 
comment: true
lang: ''
---

【注意】本文操作均有风险，楼主不对按照本帖操作所引起的后果负任何责任。可能引起的后果包括但不限于令操作者受到处分、留校察看、劝退，且我们最终也不会公布密码。

班牌是我与小伙伴们一起研究从而最后破除了它的本地设置密码。图中这个班牌较难破解，程序中没有任何明显漏洞

班牌原本的样子

![bp1](https://cdn.xtawa.top/AgACAgEAAyEGAASlhh0RAAMYaHRdzns3d96E2P9XVIGW5YfOZWsAAm2uMRt8LqFHKqAm1lEoPMQBAAMCAAN3AAM2BA.2vf189tx7k.webp "原样")

之前刚入学，发现每个班门口都有电子班牌，感觉挺新奇的。一开始并未发现它使用的是Android系统，直到有一次这个玩意卡出了文件管理（安卓5-安卓7.1.2样式的）才发现他是安卓，于是从那时起便开始研究

首先观察班牌：和多数班牌并无区别，无非是一块屏幕、一个摄像头和一个NFC模块，但是班牌软件做的简直天衣无缝，里面任何输入界面都使用的是自建输入法，没有剪切板，去掉导航键，封锁接口，万幸的是并未做进一步检测与封锁。软件几乎没有漏洞，让我们束手无策，但右上角有一个进入设置的入口可供调试。

密码输入界面

![bp4](https://cdn.xtawa.top/AgACAgEAAyEGAASlhh0RAAMZaHReEiW6853xT5Aiq16BMfLO2FcAAm6uMRt8LqFHFMajSCEVw9UBAAMCAAN3AAM2BA.39lgz5282l.webp "password_ui")

但硬件上的缺陷则让我们发掘出了办法，毕竟1+8确实配置低。之前有几次我与其他小伙伴在一个需要调用摄像头的地方多次尝试，软件意外崩溃从而弹出了切换桌面的Activity，然后在设置中打开导航键，提取了班牌软件从而为进一步破解做出准备。但在破解密码之前，我们则使用了一些悬浮球软件来辅助其它需求。

始终使用悬浮球比较无趣，且有时悬浮球也会出现找不到、被杀掉等情况，于是我们便尝试反编译软件并获取密码。

反编译过程

![bp3](https://cdn.xtawa.top/AgACAgEAAyEGAASlhh0RAAMaaHReUERIRPZKMnch2JlexudjAy4AAm-uMRt8LqFHmH1WqhWMF9MBAAMCAAN5AAM2BA.67xr2nahjv.webp "apk_code_ui")

app甚至在班牌内放了下载地址。下载apk后，首先使用apktool反编译出软件的jar，再使用jd-gui来读取MainActivity，密码则在其中。靠密码可直接进入软件设置并随意操作。


结果图

![bp_done](https://cdn.xtawa.top/AgACAgEAAyEGAASlhh0RAAMPaG-jjdHpGkzPsyA4hrtgLjmFh5AAAretMRsdWoFHP7TJ3BPg-S8BAAMCAAN3AAM2BA.39lgz5282h.webp "apksettings_ui")

![bp_done2](https://cdn.xtawa.top/AgACAgEAAyEGAASlhh0RAAMQaG-jpdmGzUlqZqJy99kL3ajTGOQAAritMRsdWoFHd6heCMq0H-QBAAMCAAN3AAM2BA.4joe5gk7dj.webp "thirdapp_ui")

<!-- ##{"timestamp":1728278302}## -->

