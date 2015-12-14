#极当推送

##需求

##解决方案

###推送通知开关存放于localStorage(isPushChecked), 初始化进入app,
首先判断插件是否存在，
|-----变量------|--值---|--备注--|
| isPushChecked | null  | 初始化默认为true |
| isPushChecked | true  | 推送开关打开     |
| isPushChecked | false | 推送开关关闭     |
window.plugins.jPushPlugin.init()
window.plugins.jPushPlugin.resumePush();
window.plugins.jPushPlugin.stopPush();
