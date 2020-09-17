# 通过PicGo和Gitee实现图床
## 图床用于在markdown文件中插入图片

首先注册一个gitee码云账号创建一个个人仓库。

仓库配置如下

![](https://gitee.com/shat412/mkimage/raw/master/img/20200914140651.png)

然后下载一个PicGo，在插件设置中搜索gitee，安装`gitee-uploader 1.1.2`,如果显示长时间不能安装的话，先下载一个
[`node.js`](https://nodejs.org/en/)
![](https://gitee.com/shat412/mkimage/raw/master/img/20200914140731.png)

下载之后再PicGo设置中找到gitee
![](https://gitee.com/shat412/mkimage/raw/master/img/20200914141245.png)
repo：用户名/仓库名称，比如我自己的仓库shat412/mkimage，找不到的可以直接复制仓库的url
![](https://gitee.com/shat412/mkimage/raw/master/img/20200914141458.png)

branch：分支，这里写上master

token：填入码云的私人令牌

path：路径，一般写上img

customPath：提交消息，这一项和下一项customURL都不用填。在提交到码云后，会显示提交消息，插件默认提交的是 Upload 图片名 by picGo - 时间

私人令牌在个人头像下设置里面安全设置，右上角点击生成新令牌
配置如下
![](https://gitee.com/shat412/mkimage/raw/master/img/20200914141812.png)

然后点击保存并保存为默认图床即可使用了

## 使用流程
把图片拖到上传区，等待上传完后，使用`Ctrl + V`粘贴到markdown文件下即可。