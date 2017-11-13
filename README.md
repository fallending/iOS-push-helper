# SmartPush

SmartPush, 一款IOS苹果推送测试程序, Mac OS下的apns工具APP

## 界面截图

![image](demo.png)


## 使用方法

1. 拖拽或者浏览测试证书和生产证书到指定输入框
	* 本机必须装有证书对应的私钥!!!!
2. 填写对应的device token  (device token 不同环境不同)
	* 获取device token
	```
	// Receive deviceToken
	- (void)application:(UIApplication *)app didRegisterForRemoteNotificationsWithDeviceToken:(NSData *)deviceToken {
    	NSString *deviceTokenString = [deviceToken description];
    	deviceTokenString = [deviceTokenStr stringByReplacingOccurrencesOfString:@" " withString:@""];
    	deviceTokenString = [deviceTokenStr stringByTrimmingCharactersInSet:[NSCharacterSet characterSetWithCharactersInString:@"<>"]];

    	// deviceTokenString 就是我们要的, 比如：ff18c50062eaa7e7787fa466295ea7bd1b301c5ad3ea6552b4fee36dd0b056d6
	}
	```
3. 填写Payload
	* apns模版
	```
	{
		"aps":
		{
			"alert":"This is some fancy message.",
			"badge":1,
			"sound": "default"
		}
	}
	```
	* 当前咱们～
	```
    {
		"aps":
		{
			"alert":
			{
				"title":"消息标题",
				"body":"消息内容"
			},
			"badge":1,
			"sound": "default"
		},
		"ext":
		{
			"pushtime":"",
			"url":"http:://打开页面的url"
		},
	}
	```
4. 选择推送环境【测试环境、生产环境】
5. 连接推送服务器
6. 发送推送
7. 手机接收推送消息
8. 可能会遇到的问题：
	* [无法连接到服务器](https://github.com/shaojiankui/SmartPush/issues/3)

## 知识点

1. [iOS开发API解读之SSL/TLS连接](http://www.jianshu.com/p/ad22f608690f)
2. [iOS开发中MQTTKit的TLS/SSL支持方案](http://www.jianshu.com/p/1c9075fe1e55)
3. [iOS开发适配HTTPS详细教程](https://www.2cto.com/kf/201611/570823.html)
4. [史上最全解析Android消息推送解决方案](http://www.jianshu.com/p/b61a49e0279f)
5. [极光推送](http://docs.jiguang.cn/jpush/client/iOS/ios_sdk/), [极光SDK](http://www.umeng.com/codecenter.html)

## 其他推送相关的项目

1. [Ionic的推送案例](https://github.com/aggarwalankush/ionic-push-base)
2. [Java发送APNs的库](https://github.com/relayrides/pushy)
3. [Redth/PushSharp, 服务器端的推送库，支持APNs，GCM](https://github.com/Redth/PushSharp)
4. [appleboy/gorush](https://github.com/appleboy/gorush), [zjnxyz/push](https://github.com/zjnxyz/push)
5. [Danny1451/ATRNotification, 自动阅读通知](https://github.com/Danny1451/ATRNotification)
6. [PerfectlySoft/Perfect-Notifications, 服务器端库，swift](https://github.com/PerfectlySoft/Perfect-Notifications)
