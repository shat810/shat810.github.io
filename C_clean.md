# C盘清理
## 转移虚拟内存
使用`win + pause`打开系统属性
![](https://gitee.com/shat412/mkimage/raw/master/img/20201008114345.png)\
点击高级系统属性\
![](https://gitee.com/shat412/mkimage/raw/master/img/20201008114707.png)\
点击性能框中的设置\
![](https://gitee.com/shat412/mkimage/raw/master/img/20201008114911.png)\
点击虚拟内存框中的更改\
![](https://gitee.com/shat412/mkimage/raw/master/img/20201008115148.png)\
点击任意一个硬盘，然后选择`系统管理的大小`，最后点击设置。
**设置完成后需要选择c盘，然后选择`无分页文件`，点击设置。**\
设置完成后，点击确定。\
![](https://gitee.com/shat412/mkimage/raw/master/img/20201008115803.png)\
重启计算机即可。
## 转移系统缓存
先在除C盘外，任意一个盘中创建一个Temp文件夹。
然后按`win + pause`打开系统属性\
![](https://gitee.com/shat412/mkimage/raw/master/img/20201008114345.png)\
点击高级系统属性\
![](https://gitee.com/shat412/mkimage/raw/master/img/20201008120959.png)\
点击环境变量\
![](https://gitee.com/shat412/mkimage/raw/master/img/20201008121210.png)
![](https://gitee.com/shat412/mkimage/raw/master/img/20201008121135.png)\
将这四个路径改为刚刚创建的Temp文件夹，点击确定即可。\
设置完成同样需要重启电脑。
## 转移文件夹位置
打开我的电脑
![](https://gitee.com/shat412/mkimage/raw/master/img/20201008121534.png)\
鼠标右键点击桌面，选择属性\
![](https://gitee.com/shat412/mkimage/raw/master/img/20201008121618.png)\
点击位置，然后把桌面的位置转移到自己创建的文件夹中即可。\
此方法同样能把，文档、音乐、视频等转移。
## 重建搜索索引
如果你经常使用windows搜索功能，会导致windows.edb变得非常臃肿，占用大量的磁盘空间。
在开始菜单的搜索栏中搜素**索引选项**\
![](https://gitee.com/shat412/mkimage/raw/master/img/20201008122142.png)
![](https://gitee.com/shat412/mkimage/raw/master/img/20201008122214.png)\
点击高级\
![](https://gitee.com/shat412/mkimage/raw/master/img/20201008122344.png)\
第一步先重建索引，然后把索引文件的位置转移到别的硬盘即可。