qrcodeSign
==========

基于微信公共账号的二维码签到工具

### 原理：
     
签到页面先去检测本地的cookie，如果本地cookie和通过授权页面设置的不一致，视为未授权设备，直接跳转到指定的页面；如果一致，拉取用户的报名信息。
     
### 关键点：
     
1. 微信内置的webview支持cookie和页面之间的JS跳转
2. 微信扫一扫支持直接跳转到扫描结果

### 风险点：
     
1. 生成二维码的接口都是调用第三方，不是自己控制，可能会挂掉
2. 生成的二维码一般第三方都会有图片保存，不够安全

### 缺点：
     
1. 使用微信扫一扫要先登陆微信，如果设备较多，需要足够的微信账号

### 后续优化：
    
1. 目前接口直接用了openID，没有做进一步验证，可以增加一个签名，例如openID和appid字典序MD5增加在入场券的二维码中，获取签到信息的时候后台验证一下
2. 出现签到失败可以给后台发送一条告警，及时发现和定位异常
3. 自己写一个js二维码
    
### demo 使用：[点击查看]( https://blog.bihe0832.com/wechar_sign_with_qrcode.html)

### 代码结构：

     — conf:二维码签到demo中所有的核心配置，更改配置以后即可为你所用。
     — css:页面css
     — images:资源图片
     — js:页面js
     — intro.php:会议介绍页面，未授权设备扫码后跳转页面
     — my_bak.php: 使用公司内部生成二维码接口生成二维码入场券页面
     — my.php: 使用外部第三方生成二维码接口生成二维码入场券页面
     — sign.php: 授权后设备扫描入场券以后跳转页面
     — signPre.php: 设备授权
     — signAfter.php: 设备取消授权
