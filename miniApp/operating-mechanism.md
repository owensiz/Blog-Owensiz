# 小程序运行机制

> https://developers.weixin.qq.com/miniprogram/dev/framework/runtime/operating-mechanism.html

## 1 前台/后台状态
 
- 启动，界面展示 -> 进入**前台** 
  - -> 右上角胶囊按钮关闭小程序/设备home键关闭微信 -> 进入**后台** 
    - -> 再次进入微信/再次打开小程序 -> 进入**前台** 
    - -> 很久没有再进入小程序/系统资源紧张 -> 小程序**被销毁** 



## 2 小程序启动

### 2-1 冷启动（重新加载启动）
  - 首次打开
  - 销毁后被打开

### 2-2 热启动（未重新启动，只是从后台进入前台）
  - 已经打开过小程序，一定时间内（此时小程序未被销毁）重新打开，


## 3 小程序销毁时机

- 进入后台很久都未被重新打开
- 占用系统资源过高，被系统销毁/被微信客户端主动回收
  - iOS上，目前为5s内连续两次或以上，收到系统内存告警，会主动销毁
  - 可使用 wx.onMemoryWarning 监听内存告警事件，进行必要的内存清理。


## 4 启动场景分类
- A. 打开首页，场景值详见链接
- B. 打开某个指定页面


## 5 热启动逻辑
小程序在热启动时，可能需要立刻跳转到别的页面，如点击分享卡片进入小程序时。此时可能会自动产生一些页面跳转。
依赖于 4，我们可以列出下表


上一次启动场景 | 当前启动场景 | 效果
----------- | ---- | ---
A | A | 保留原状态
B | A | wx.reLaunch()到首页，即清空原来页面栈，打开首页
A | B | wx.reLaunch()到指定页，即清空原来页面栈，打开该页
B | B | wx.reLaunch()到指定页，同上

## 6 A 类场景的重新启动策略
## 7 退出状态
