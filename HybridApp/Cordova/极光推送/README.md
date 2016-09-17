#极当推送

##需求

###用户点击推送消息，跳转到指定页面。

###用户登录，打开推送。

###用户退出，关闭推送。

###定制推送时间，开始时间-结束时间。

###设备禁用

打开应用并且用户处于登录状态和推送信息是打开状态，才能接收推送信息。

###设备打开

应用推送通知状态打开并且用户处于登录状态，接收推送信息。

###推送对象：广播、设备标签(Tag)、设备别名(Alias)、Registration ID

##解决方案

###前提条件：推送通知开关根据应用来。

###推送通知开关存放于localStorage(isPushChecked), 初始化进入app,

首先判断插件是否存在，
|-----变量------|--值---|--备注--|
| isPushChecked | null  | 初始化默认为true |
| isPushChecked | true  | 推送开关打开     |
| isPushChecked | false | 推送开关关闭     |
window.plugins.jPushPlugin.init()
window.plugins.jPushPlugin.resumePush();
window.plugins.jPushPlugin.stopPush();
