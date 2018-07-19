# sis
simple image server 为简单而生

写在之前：
如今的互联网时代图片存储服务随处可见，实现方案也是五花八门，那么有没有一个开袋即食的方案呢？粗略找了一圈，zimg(https://github.com/buaazp/zimg) 似乎是我最想要的，但一看长长的依赖安装列表顿时望而却步，虽然开袋即可吃了，但这袋子也太难开了点，手撕牙咬都不行，感觉要上剪刀。
于是sis诞生了，如果你也有这需求，赶紧拿走，别无他求，给加个星吧。

sis宪法：
1.程序安装不需前置依赖
2.程序编译不需前置依赖
3.程序启动不需配置文件

sis实现：
既然框架已定，很自然的选择了GO来实现。感觉实现这么一个简单功能不会需要多少代码量，那么开始吧。。。。。。
上传接口：使用HTTP post
下载接口：使用HTTP get
文件存储：使用文件的MD5码拆解后作为目录名，MD5码作为文件名

1.0 模仿zimg功能实现：
图片上传
图片下载
图片缩放

cache有木有？可以有，但现在木有，2.0吧
分布式有木有？可以有，但现在木有，3.0吧
那4.0干啥呢？山还不够多么，不会有事了。
