# 小程序生命周期钩子罗列

## 程序级别
### App() 

App() 构造函数来创建小程序
 - onLaunch 小程序初始化
 - onShow 小程序启动 / 小程序切前台
 - onHide 小程序切后台
 - onError 错误监听
 - onPageNotFound 页面不存在监听

### getApp()
getApp()来获取实例 