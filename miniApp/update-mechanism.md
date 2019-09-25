# 小程序更新机制

> https://developers.weixin.qq.com/miniprogram/dev/framework/runtime/update-mechanism.html

## 1 小程序未启动时

- 如果用户本地有旧版本，此时打开可能还是旧版本。
- 微信有若干个时机检查本地缓存的小程序的更新，若有则会静默更新。
- 开发者发新版本，不会立刻影响所有用户。但最差24h内下发新版本信息。



## 2 小程序启动时
- 每次冷启动，会检查更新。若有更新，**异步**下载新版本，同时用**本地包**进行启动。
- 新版本下次**冷启动**才能用上。
- 如果需要马上应用最新版本，可以使用 wx.getUpdateManager API 进行处理。
