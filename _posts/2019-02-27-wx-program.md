---
layout: post
title: '微信小程序'
subtitle: ''
author: 'Jevaeson'
header-img: 'img/post-bg-extgen-web-pwa.jpg'
header-mask: 0.4
catalog: true
tags:
  - Wechat
  - 笔记
---

# 基本功能

网络（手机网络）

媒体（照片相机）文件操作

数据：位置定位、用户数据、设备信息

微信：支付、生物识别（指纹）、微信运动信息、微信卡券、客服、二维码（识别）

社交:微信转发、qq转发

# 层级结构

1. app层

   整体小程序配置
   
2. page层（单一页面）

   wxml(html) wxss(css) js json
   
# 介绍app.js

| 名称 | 作用 | 备注 |
| :------:| :------: | :------: |
| onLaunch | 小程序启动时候触发的函数 | （相当于vue中的created）|
| globalData | 全局数据 | 相当于vuex、redux的全局数据 |

# 介绍wxml

| 标签 | 对应html | 备注 |
| :------:| :------: | :------: |
| `<view></view>` | `<div></div>` | / |
| `<button></button>` | `<button></button>` | / |
| `<image></image>` | `<img/>` | 属性src内添加url |
|`<text></text>`|`<span></span>`|所有文字内容都可以写在这里|
|`<icon></icon>`| / | 微信图标：拥有type属性 |
|`<progress></progress>`|/|进度条|
|`<picker></picker>`|/|从底部弹起的滚动选择器。通过mode来区分，分别是普通选择器，多列选择器，时间选择器，日期选择器，省市区选择器，默认是普通选择器|
|`<navigator></navigator>`|`<a></a>`|/|
|`<switch />`|/|开关|
|`<audio></audio>`|`<audio></audio>`|音频|
|`<video></video>`|`<video></video>`|视频|
|`<camera></camera>`|/|系统相机|
|`<map></map>`|/|地图|
|`<canvas></canvas>`|`<canvas></canvas>`|画布|
|`<slider></slider>`|/|音量|
|`<radio-group></radio-group>`|/|单选群组|
|`<checkbox-group></checkbox-group>`|/|多选群组|



