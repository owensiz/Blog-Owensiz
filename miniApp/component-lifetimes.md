# 组件生命周期钩子罗列

## 组件级别

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
