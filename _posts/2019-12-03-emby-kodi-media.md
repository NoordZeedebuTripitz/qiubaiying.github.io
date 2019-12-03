---
layout:     post
title:      利用Emby以及Kodi搭建本地媒体库的简单尝试
subtitle:   动手远比想像要容易
date:       2019-12-03
author:     纪
header-img: img/IMG_1055.PNG
catalog: true
tags:
    - 生活
---

>标题背景是因为太晚了所以随便扔了一张上去的=.=

两天前，人生第一台属于自己的平板电脑——surface go到货了，机身造型比我想象的要好，屏幕质量比我想象的要高，运行速度比我想象的要...呃，正常吧，毕竟早有心理准备了，也还是可以接受，非要挑剔一下微软的品控的话，就是锁定键略松动，不过无伤大雅，调试了半天时间，装上一些必备软件，就可以拿来"玩"了

当手头上有了两台windows/andriod系统的时候，第一件事肯定是要做资源共享了，特别是在surface go只有128G内存的情况下，视频和图片资源的共享还是很必要的，再加上校园网一个月20块不嫖白不嫖，于是就有了这个搭建本地媒体库的想法

于是之后两天，趁着课程不是很多，摸索着搭建了以笔记本为本地服务器，surface为客户端的初级平台，传输速度也比想象中的要好得多

![](https://raw.githubusercontent.com/NoordZeedebuTirpitz/pic/master/IMG_1076.JPG)

至于这些步骤也都会在下文深入浅出，一一介绍

### 服务端：Emby

首先是建立本地服务器，说白了就是也下载个小程序，让它在后台运行着就完事了

目前市面上成熟的本地媒体库工具，无外乎Emby与Plex

在浏览评价以及实际做了些对比后，发现Emby有能够集成的官方插件库，较为简单和便捷，同时还有一个由用户社区做出来的开源分支，一定程度上保证了在Emby上的数据的后路，所以这里选择了Emby作为服务端应用，开始着手建立本地服务器

打开[Emby的官网](https://emby.media/download.html)，按照想要作为服务器的机器的系统选择对应的Emby服务端插件并安装

![](https://raw.githubusercontent.com/NoordZeedebuTirpitz/pic/master/Emby%20Server%20for%20Windows%20-%20Google%20Chrome%202019_12_2%2012_41_43.png)

安装完成后会弹出设置引导，首先是选择语言，这里就选择`Chinese Simplified（简体中文）`，然后`next→`

![](https://raw.githubusercontent.com/NoordZeedebuTirpitz/pic/master/Emby%20Server%20for%20Windows%20-%20Google%20Chrome%202019_12_2%2012_46_03.png)

创建一个管理服务器的用户，填入用户名以及密码，下面的可以不填

![](https://raw.githubusercontent.com/NoordZeedebuTirpitz/pic/master/Emby%20-%20Google%20Chrome%202019_12_3%2020_48_19.png)

下一页的话，暂时先不用添加媒体库，直接点`next→`

元数据语言这里，还是选择`Chinese Simplified`，国家随便填一个吧，反正我没找到China，也不会有太大影响

之后默认`next→`

点选`同意条款`然后`next→`

这样，最基础的Emby服务端就建立完成了

在浏览器中输入Emby服务端本地IP+:8096，就能进入Emby的主页面

进入页面后，点击左上角的“三”→`管理Emby服务器`进入控制台

![](https://raw.githubusercontent.com/NoordZeedebuTirpitz/pic/master/%E6%8E%A7%E5%88%B6%E5%8F%B0%20-%20Google%20Chrome%202019_12_3%2023_51_19.png)

左侧的项目可以都浏览一遍~~虽然有的我也看不懂就是了~~

至于`插件`选项里的东西，光是做本地媒体库的话也都用不到，于是我清理成了如下内容（BD的话以后没准用得上）

![](https://raw.githubusercontent.com/NoordZeedebuTirpitz/pic/master/555.png)

然后回到左侧点选`媒体库`，点击添加媒体库

内容类型随意，因为我没做有关元数据的抓取设置~~懒得做~~，然后点击文件夹旁边的“+”，添加文件，诸如视频，图片，其他保持默认，点击`确定`，等待转码完成，这个过程还是很快的

届时，本地媒体库已经可以使用了，抽出在同一网络环境下的另一台设备（这里经尝试，证明任何校内有网络覆盖的地点包括不同校区的JLU.PC/NET/TEST及5G都属于同一网络环境，都可以连接本地服务器），在浏览器输入控制台页面绿色的局域网访问网址，就能连接上服务器了，在这里有一点要注意的，就是Emby**强大的多用户管理功能**

用户在服务端安装界面填入的账号，就相当于这个服务器的管理者，拥有服务器的最高权限，并且可以添加额外用户，在`用户页面`，点击“+”，填入一个名字，点击`保存`，就可以使用了

这个功能强大在哪里呢，点击创建完后的用户，你可以自定义这个用户的媒体库访问权限，保证用户拥有“专属”的媒体库

而在服务端，管理员甚至可以看到其他用户连接Emby时的进程，还可以通过控制台远程操作暂停/播放/停止客户端正在进行的视频，还能发消息~~祖安玩家请求单方面互动~~

以上，服务端配置基本完毕，偷懒的话可以就这样在多设备上通过浏览器进行浏览

### 客户端:Kodi

鉴于Emby虽有官方客户端，但是既收费又屑，所以只好以贫穷催动技术发展，掌握通过Kodi插件作为客户端，实现0成本的本地解码播放操作

注:Kodi是主要针对视频播放的插件，其他文件还是推荐浏览器打开和保存

依旧是打开[Kodi的官网](https://kodi.tv/)，根据想要运行Kodi的设备系统，点选相应图标，下载完成，安装，打开

首先进入Kodi的`系统设置`

![](https://raw.githubusercontent.com/Pockies/pic/master/741f9461ly1g1cyrpmvvnj216a0nr1kx.jpg)

点选`Interface`

![](https://raw.githubusercontent.com/Pockies/pic/master/741f9461ly1g1cyroa1l6j216a0npkg5.jpg)

在`Skin`界面，将`Fonts`后面的选项修改为`Arial based`

![](https://raw.githubusercontent.com/Pockies/pic/master/741f9461ly1g1cyrr33t1j216a0nq1kx.jpg)

然后选择`Skin`下面的`Regional`界面，将`Language`修改为`Chinese（simple）`

![](https://raw.githubusercontent.com/Pockies/pic/master/741f9461ly1g1cyro61wlj216a0nmhdh.jpg)

**以上的顺序一定不要颠倒，Kodi的默认字体无法显示简体中文，先改语言只会让界面语言变成乱码**

回到`系统设置`，进入`文件管理`

![](https://raw.githubusercontent.com/Pockies/pic/master/741f9461ly1g1cyrpj1myj216a0nmha5.jpg)

点击`添加源`

![](https://raw.githubusercontent.com/Pockies/pic/master/741f9461ly1g1cyroa1q3j216a0ntk6a.jpg)

输入Kodi提供的官方路径`http://kodi.emby.media`，然后任意命名就可以，我直接命名为emby，点击确定

![](https://raw.githubusercontent.com/Pockies/pic/master/741f9461ly1g1cyrnwjkxj216a0nktcx.jpg)

回到`系统设置`，进入`系统`，选择`插件页面`，打开`未知来源`选项

![](https://raw.githubusercontent.com/Pockies/pic/master/741f9461ly1g1cyrpn0emj216a0nmhd1.jpg)

继续回到`系统设置`，进入`插件`，点击`从zip文件夹安装`

![](https://raw.githubusercontent.com/Pockies/pic/master/741f9461ly1g1cyz9m5dmj21480nle08.jpg)

进入刚刚添加的文件夹emby

![](https://raw.githubusercontent.com/Pockies/pic/master/741f9461ly1g1cyz9d0hvj216a0nodmf.jpg)

点击`repository.emby.kodi-1.0.4.zip`，安装插件库

![](https://raw.githubusercontent.com/Pockies/pic/master/741f9461ly1g1cyz9cx5sj216a0npgrv.jpg)

**如果找不到zip文件，请从添加源处重试**

等待插件安装完毕，点击`从库安装`

![](https://raw.githubusercontent.com/Pockies/pic/master/741f9461ly1g1cyza41spj216a0nsb0e.jpg)

在目录里找到`Kodi Emby Addons`→`视频插件`→`Emby`

点击右下角`安装`

![](https://raw.githubusercontent.com/Pockies/pic/master/741f9461ly1g1cyza7t71j216a0noaz7.jpg)

安装完后便弹出配置对话框

这里如果没有自动搜索到本地服务器，需要点击下面的`Manually add server`,手动输入自己的服务端的IP与端口，IP即XXX.XXX.XXX.XXX，端口8096

尝试连接后成功，这里再登录进入Emby，便与本地服务器连接成功

之后的设置可以自行选择，个人全部`否`了

最后会需要将Emby同步到Kodi的媒体库，这里点击`Proceed`，然后选择想要同步的媒体库，按确定后进行同步

![](https://raw.githubusercontent.com/Pockies/pic/master/741f9461ly1g1cyz9n5tej216a0no4as.jpg)

返回Kodi主页，由于我上传的视频以及图片都没有提取元数据，所以这些东西需要任意打开右侧一个类别，点开`...`选择`Emby`文件夹打开，就会发现你的文件都安静的躺在这里，随意点开就可以浏览了

### 小结

至此，本地媒体库以及客户端已经基本设置完成，折腾也可以告一段落了，在过程中也可以发现Emby以及Kodi都有很多便捷的功能我还没有发掘，针对Kodi客户端的改进也可以继续，不过这里暂且告一段落，因为这反人类操作的玩意确实整得我脑壳疼，并且说好的blog评论功能到现在也没有实装，blog页面也还有一些bug还没改（比如翻页的手感很黏，应该是右侧多出来的一个滚动条造成的），所以，摸了

其实以上这些都是网络上写烂了的东西，我能整理出这篇傻瓜教程靠的也是“前人栽树，后人乘凉”，无非就是写得罗嗦了点，还多了些自己踩的坑，顺便，由于要找各种资料，一直在墙内外爬来爬去，所以不敢保证本篇方法在纯国内网络环境下的成功进行

不过比较好的一点就是服务端，也就是我的笔记本不需要进行校园网登录，只要插着网线，连上了JLU.PC，就能使用，毕竟是走校内网络的原因...~~白嫖网络大成功~~

并且EmbyServer对内存的占用也可以接受，所以平时一直挂后台开启服务器也是可行的

![](https://raw.githubusercontent.com/NoordZeedebuTirpitz/pic/master/277.PNG)

大概就这些，累死，歇了
