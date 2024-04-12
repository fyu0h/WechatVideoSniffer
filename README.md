# 最新版本

重构了一个新版本，新版本没有开源代码，但依旧可以免费使用(需要关注公众号)

https://github.com/kanadeblisst00/WechatVideoSniffer2.0 

# WechatVideoSniffer

微信视频号PC版视频地址嗅探器

本项目采用[aardio](https://www.aardio.com/)编程语言开发，

本项目Fork自[WechatVideoSniffer](https://github.com/xuncv/WechatVideoSniffer)，然后根据看雪的[一篇文章](https://bbs.kanxue.com/thread-279740-1.htm)增加了解密视频的逻辑

后面这个控制台是debug版本打印错误日志用的, 另一个版本没有
![](http://cdn.ikanade.cn/20240128132804.png)

## 原理

使用FiddlerCore .Net组件，注册系统代理，监听主机的http/https请求，从而匹配出微信视频号视频的地址, 然后下载并解密

工具原理说明: [写一个视频号下载工具](https://mp.weixin.qq.com/s/sjjsKC9UlK7ZBoeE2JmZIQ)

## 使用方法

**先操作注意事项第一点**。然后以管理员权限运行该软件，先点击监听(第一次会提示安装证书)，然后打开一个视频，就能在文本框看到监听到的下载链接和弹出的下载进度条。只要拦截到就会打印链接，并自动下载到当前软件的`cache`目录下

注意事项：

1. 如果是第一次使用软件，需要先退出微信，然后点击`删除缓存`按钮，等待删除完成。也可以手动去`C:\Users\你的用户名\AppData\Roaming\Tencent\WeChat\radium\web\profiles`删除目录下的所有文件，原因见上面的文章里。应该只需要第一次使用的时候删除缓存目录
2. 点击监听后，最好只打开需要下载视频的详情页(先分享给文件传输助手打开)，不要去打开列表页，不然会有很多的视频跳出来，会有意想不到的bug，这种我不去解决。
3. 为避免下载链接因长时间未响应导致下载中断，过程中会持续hook界面按钮，确保页面响应
4. 如果报毒的话，这个可以自己根据源码编译一个(应该也是报毒的)，免杀也是门技术，我不会

## 常见下载问题

1. 没有以管理员权限运行软件，无法设置系统代理(可以在任务栏搜索 代理，看看代理是否设置成功)
2. 缓存未删除成功，需要手动进入`C:\Users\你的用户名\AppData\Roaming\Tencent\WeChat\radium\web\profiles` 删除，有人的电脑在`WeChat\radium\web`目录下没有profiles目录，把`WeChat\radium\web`下的文件和文件夹都删了才成功拦截到。这些文件夹都是微信浏览器的缓存文件，删除后会重新生成，所以不用担心啥


## 待更新的问题

- 预览的视频也会被下载，后面看看能不能过滤掉
- 有些视频会出现 not enough memory，暂未找到原因
- 取消自动下载，设置成手动下载

## 软件获取

自行编译工程或者到`[视频号下载助手](https://github.com/kanadeblisst00/WechatVideoSniffer/releases/download/Release/_20240201.zip)`下载

两个文件区别只在于调试会打开控制台窗口，用于打印异常

如果杀毒软件报毒请添加到白名单或者自己编译一个(应该也是报毒)

## 联系方式

建了个群, 有问题及时反馈

![](http://cdn.ikanade.cn/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20240312154230.jpg)

如果二维码失效了，可以加我好友`kanadeblisst`，备注`视频号群`

## 感谢

- [微信视频号视频加密逆向](https://bbs.kanxue.com/thread-279740-1.htm)
- https://github.com/xuncv/WechatVideoSniffer
