# 微信小程序路由和页面生命周期
> 参考：https://developers.weixin.qq.com/miniprogram/dev/api/route/wx.switchTab.html
## 路由
### 关注点： 
> 跳转是否可带参，跳转是否关闭页面（包括当前页面，其他页面，tab类页面），跳转是否保留当前页面++


### 路由方式
- wx.switchTab
不允许带参，跳转到tabBar页面，并关闭其他tabBar
```
wx.switchTab({
  url: '/index'
})
```
- wx.reLaunch
可带参，关闭所有其他，打开某个页面
```
wx.reLaunch({
  url: 'test?id=1'
})
```
- wx.redirectTo
可带参，关闭当前页，跳到除了tabBar之外的某个页面
```
wx.redirectTo({
  url: 'test?id=1'
})
```
- wx.navigateTo
可带参，保留当前页，跳到除了tabBar之外的某个页面。可使用wx.navigateBack返回。页面栈最多10层。
```
wx.navigateTo({
  url: 'test?id=1'
})
```
- wx.navigateBack
参数为delta，表返回的层数。关闭当前页，返回上一级或者多级页面。
> getCurrentPages 可得当前的页面栈。不会触发上级页面的onLoad，只会触发onShow。
```
wx.navigateBack({
  delta: 2
})
```

