---
layout: post
title: '微信小程序'
subtitle: ''
author: 'Jevaeson'
header-img: 'img/post-bg-nextgen-web-pwa.jpg'
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
|`<picker></picker>`|/|从底部弹起的滚动选择器|
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

# rpx

横向的rpx：微信小程序将整个宽度划分为750个rpx。

```css
header{
 width:750rpx;
}
```

750rpx:代表全屏。

高度写成响应式要用vh单位。%是根据宽度来计算的。

# 小程序中的JS

index.js

```js
Page({
data:{
a:0,
b:false
}
})
```

index.wxml

```js
<text>{{a}}</text>//0
<view>
    <button size='mini' class="{{b?'active':''}}">实现按钮消失出现</button>
  <button wx:if="{{b}}" size='mini'>我是测试按钮</button>
  </view>
  ```
  
列表渲染
```js
Page({
data:{
arr:[1,2,3,4,5,6]
}
})
```
```js
<view wx:for="{{arr}}" wx:key="{{index}}">{{item}}</view>
```

事件绑定

运用 this.setData 方法来修改data

```js
 change(){
    this.setData({
      b:!this.data.b
    })
  },
```

学习了以上获取、修改局部data的值，那么全局data如何获取和修改呢？

1. 通过 getApp()方法获取全局对象

```js
cosnt app = getApp()
```

2. 通过全局对象 globalData 属性获取全局对象。

现在若有一个全局数据 c

```js
app.globalData.c
```

定义一个局部data值等于以上。

经过以上处理，我们就可以使用全局数据。

# 新建页面

在微信开发者工具中

新建目录->新建pages->自动生成

默认地址从 pages/index/

```js
<navigator url="../user/user">去user</navigator>
```

# picker

首先要谨记的是，picker是需要组件来触发的，所以picker里一定要写view组件。

今天要写的是利用picker选择性别功能

在这里我们选择普通选择器即可，range属性是我们存放选择数组的地方，value属性是存放数组下标的地方（默认为0）。

index.wxml

```js
<picker range="{{sexArr}}" value="{{sexInd}}" bindchange="selectSex">
<view >
性别{{sexArr[sexInd]}}
</view>
</picker>
```

index.js

```js
data: {
    date: '',
    sexArr:['男','女'],
    sexInd:0,
  },
   selectSex(e){
    this.setData({
      sexInd:e.detail.value
    })
  },
```

# 页面中的生命周期

| 名称 | 作用 |
| :------:| :------: | 
|onLoad()|监听页面加载|
|onReady()|监听页面初次加载完成|
|onShow()|监听页面显示|
|onHide()|监听页面隐藏|
|onUnload()|监听页面卸载|
|onPullDownRefresh()|监听用户下拉操作|
|onReachBottom()|页面上拉触底处理函数|
|onShareAppMessage()|用户点击右上角分享|

# 小程序常用的界面交互

| 名称 | 作用 |
| :------:| :------: | 
|wx.showLoading()|wx.showLoading()|
|wx.hideLoading()|关闭 loading 提示框|
|wx.showToast()|显示消息提示框|
|wx.hideToast()|关闭消息提示框|
|wx.showModal()|显示模态对话框|
|owx.showActionSheet()|显示操作菜单|

# 获取使用者的信息

1. 使用 Button 按钮

* 给 button 按钮添加一个属性 open-type='getUserInfo'

* 绑定一个getUserInfo事件处理 bindgetuserinfo="事件"

* 事件函数的第一个参数就是用户信息，必须同意授权

2. 使用open-data标签

* 添加type属性



