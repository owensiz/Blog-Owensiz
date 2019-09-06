# 微信小程序生命周期钩子罗列

## 页面生命周期 

### 所在位置： 
1. 指南 - 小程序框架 - 页面生命周期 + 路由方式
2. 框架 - 框架接口 - 页面 - Page （详细）
### 罗列：
- onLoad
- onShow
- onReady
- onHide
- onShow
- onUnload
----
> 其他钩子
- onPullDownRefresh
- onReachBottom
- onShareAppMessage
- onPageScroll
- onResize
- onTabItemTap （当前是 tab 页时，点击 tab 时触发）
> 页面路径 Page.route
```
Page({
  onShow: function() {
    console.log(this.route)
  }
})
```
> 

### 触发时机： 
- onLoad(Object query)。
  - 页面加载时触发。一个页面只会调用一次
  - query	Object	打开当前页面路径中的参数
- onShow
  - 页面显示/切入前台时触发。
- onReady() 
  - 页面初次渲染完成时触发。一个页面只会调用一次
  - 对界面内容进行设置的 API ，请在onReady之后进行。
  - 如wx.setNavigationBarTitle
- onHide()
  - 页面隐藏/切入后台时触发。 
  - 如 wx.navigateTo 或底部 tab 切换到其他页面，小程序切入后台等。
- onUnload()
  - 页面卸载时触发。
  - 如wx.redirectTo或wx.navigateBack到其他页面时。
- 一般新页面都会 onLoad，onShow， 除了wx.navigateBack，只触发onShow，不触发onLoad
- tab切换的触发，参见表格

### 路由相关的tips 
> 重要！
- navigateTo, redirectTo 只能打开非 tabBar 页面。
- switchTab 只能打开 tabBar 页面。
- reLaunch 可以打开任意页面。
- 页面底部的 tabBar 由页面决定，即只要是定义为 tabBar 的页面，底部都有 tabBar。
- 调用页面路由带的参数可以在目标页面的onLoad中获取。


## 组件生命周期 

### 所在位置： 
指南 - 自定义组件 - 组件生命周期 
### 罗列：
#### 定义生命周期
- created *
- attached *
- ready
- moved
- detached *
- error
```
// 自小程序基础库版本 2.2.3 起，组件的的生命周期也可以在 lifetimes 字段内进行声明（这是推荐的方式，其优先级最高）。
Component({
  lifetimes: {
    attached: function() {
      // 在组件实例进入页面节点树时执行
    },
    detached: function() {
      // 在组件实例被从页面节点树移除时执行
    },
  },
```
#### 组件所在页面的生命周期
- show
- hide
- resize 

```
Component({
  pageLifetimes: {
    show: function() {
      // 页面被展示
    },
    hide: function() {
      // 页面被隐藏
    },
    resize: function(size) {
      // 页面尺寸变化
    }
  }
})
```
