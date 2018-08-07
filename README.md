# sis
simple image server 为简单而生

1.0版已诞生，除去graphics包，主体程序只有469行，版本特性：        
1. 实现文件上传接口，可支持一次提交多个文件。上传完成后服务器将返回json格式的数组，包含原始文件名和对应的MD5码   
2. 实现根据MD5码下载接口。如果发生MD5碰撞，此接口将返回找到的第一张图          
3. 实现根据MD5码和原始文件名下载接口    
4. 实现各下载接口对应的缩放接口           

关于原始文件名：    
sis上传下载都可带上原始文件名，如此实现的目的是防止MD5碰撞的发生，即使两副图像的MD5码相同，只要原始文件名不同，也不会发生冲突   

关于graphics包：    
由于官方发行包中暂无实现图像缩放功能的包，找了个半官方版本阉割后直接内置到sis中（https://code.google.com/archive/p/graphics-go/)

简易使用指南：    
1. 下载安装golang(https://golang.google.cn/)    
2. go get github.com/DDHax/sis    
3. cd $HOME/go/src/github.com/DDHax/sis
4. go build sis.go   
5. nohup ./sis &

此时服务已启动，可以使用sis test模块测试每个接口：   
cd test/client/  
go test -v   
全部PASS则说明sis已经在正常工作啦  
另外test中的uplaod.html可以在本地用浏览器打开测试单文件上传功能，前端功力有限，丑丑的仅着参考 


2018/8/7的华丽分割线*********************************************************************************           

sis背景：         
如今的互联网时代图片存储服务随处可见，实现方案也是五花八门，那么有没有一个开袋即食的方案呢？粗略找了一圈，zimg(https://github.com/buaazp/zimg) 似乎是我最想要的，但一看长长的依赖安装列表顿时望而却步，虽然开袋即可吃了，但这袋子也太难开了点，手撕牙咬都不行，感觉要上剪刀。
于是sis诞生了，如果你也有这需求，赶紧拿走，别无他求，给加个星吧。

sis宪法：           
1. 程序安装不需前置依赖     
2. 程序编译不需前置依赖        
3. 程序启动不需配置文件          

sis实现：      
为了遵守宪法，似乎用GO实现是最好的选择。预计实现这么一个简单功能不会需要多少代码，那么开始吧。。。。。。      
上传接口：使用HTTP post       
下载接口：使用HTTP get       
文件存储：使用文件的MD5码拆解后作为目录名，文件原始文件存储在src目录，缩放后的文件根据尺寸单独建目录         

sis 1.0 将要实现的功能：       
图片上传     
图片下载     
图片缩放        

sis未来：     
cache有木有？可以有，但现在木有，2.0吧      
分布式有木有？可以有，但现在木有，3.0吧            
那4.0干啥呢？山还不够多么，不会有事了。       
