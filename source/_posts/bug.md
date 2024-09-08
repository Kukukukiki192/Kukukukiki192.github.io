---
title: 问题记录
date: 2023-09-13 01:16:56
tags: [bug]
index_img: /img/bug.png
banner_img: /img/mitsuki.png
---
> [CSDN问题记录_Bug](https://blog.csdn.net/qq_43775855/category_11481883.html?spm=1001.2014.3001.5482)

# 获取网站图标

1. 直接在网址后加 `/favicon.ico` 可获得大部分网站的图标，如

   <div align="left">
      <a href="https://www.baidu.com/favicon.ico">baidu.com/favicon.ico</a>
      <span>&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;</span>
      <a href="https://www.runoob.com/favicon.ico">runoob.com/favicon.ico</a></br>
      <img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230413191006012.png" width=35% />
      <img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230413191914276.png" width=38%/>
   </div>

2. F12查看网页源代码header标签

   <div align="left">
      <img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230413191459468.png" width=80%/>
      <img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230413191340704.png" width=19%/>
   </div>
   
   

   有的需要网站和图标链接拼接才能找到

   <img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230413191605912.png"/>
   <img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230413191726787.png"/>

# [公司里开发用的机器，虚拟机、网络、转发、ssh连接、远程桌面、远程开机……等一系列骚操作的操作概述](http://www.taodudu.cc/news/show-4707756.html?action=onClick)

# Mac

## 没有右键打开终端功能

可以通过`uTools App`的功能点击鼠标中键打开该路径下的终端

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug10.png)

## 启动台App图标显示 ‘❔’

启动台上的App图标显示❔通常表示 macOS 无法找到或加载该应用程序. 这可能是由于应用程序文件损坏、删除或移动，或者与应用程序的关联数据出现问题导致的.

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug7.png)

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug8.png)

```bash
defaults write com.apple.dock ResetLaunchPad -bool TRUE # 重置启动台
killall Dock # 重启桌面
```

解决✅

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug9.png)

## 以时间格式重命名图片

> [ExifTool官网](https://exiftool.org/)   [exiftool Application Documentation](https://exiftool.org/exiftool_pod.html#writing_examples)

使用 exiftool 工具更改文件名. 注意替换 `DIR` 路径，这将把指定目录下所有文件的文件名更改为类似 `20240202_123045-1.jpg` 的格式，其中包含了照片的创建日期和时间信息

```bash
brew install exiftool
exiftool '-FileName<CreateDate' -d "%Y%m%d_%H%M%S%%-c.%%e" DIR
# DateTimeOriginal图片原始拍摄时间 CreateDate图片创建时间 FileModifyDate图片修改时间 AllDates这3个tag的快捷方式tag
# -d	设置日期/时间的格式
# %Y%m%d_%H%M%S	具体的日期/时间组织格式
# %%-c	若拍摄日期和时间相同就添加一个顺序号
# %%e	保留原图片的扩展名
```

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/%E6%88%AA%E5%B1%8F2024-02-03%2012.00.49.png)

Q：`No writable tags set` 说明该照片没有tag `CreateDate`，不能被重命名

A：参考 [Renaming and/or Moving Files](https://exiftool.org/filename.html)，可使用其它的 `DateTimeOriginal` 或 `FileModifyDate` tag

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20240203115522399.png)

为方便使用合适的时间tag批量重命名图片，用以下方式，tag往左覆盖有效

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20240203131526301.png)

```bash
exiftool -d "%Y%m%d_%H%M%S%%-c.%%e" '-FileName<FileModifyDate' '-FileName<CreateDate' '-FileName<DateTimeOriginal'  DIR
```

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20240205011925826.png)

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20240205143440097.png)

Q：用 exiftool 重命名截图后，显示的不是原始截图时间，而是编辑截图后的修改时间

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug11.png)

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug12.png)

## 相册拖出的照片原始拍摄时间会变为拷贝时间

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/Snipaste_2024-02-06_13-12-15.png)

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/Snipaste_2024-02-06_13-15-04.png)

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20240206165706784.png)

## 时间机器备份

> 参考：[macos下的容器、宗卷、分区的主要区别及硬盘分区建议](https://zhuanlan.zhihu.com/p/596119469)  [Mac磁盘格式化、分区教程](https://blog.csdn.net/zjj778899/article/details/124911566?ops_request_misc=&request_id=&biz_id=102&utm_term=macos下的容器、宗卷、分区的区别&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-124911566.142%5Ev99%5Epc_search_result_base6&spm=1018.2226.3001.4187)

先抹掉磁盘，格式选择适用于`macOS`的`APFS`

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug13.png) 

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug14.png)

设置时间机器备份的大小为Mac硬盘的1.5倍，可做一份备份多点空余

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug15.png)

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug16.png)

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug17.png)

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug18.png)

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug19.png)

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug20.png)

自动备份太多了，我选择手动备份 点`+`选择不备份的文件

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug21.png)

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug22.png)

添加`Windows`分区，选择`ExFAT`格式

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug23.png)

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug24.png)

备份完成✅ 第一次比较久，之后会在有更改的情况下追加备份，未更改部分不动

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug25.png)

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug26.png)

## 域名网站在其他浏览器上显示为安全连接，但在Safari上显示不安全

<div>
<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug53.png" /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug52.png" />
</div>

> ChatGPT

如果你的个人博客在其他浏览器上显示为安全连接，但在Safari上显示为不安全，这可能有几个原因。以下是一些可能的解决方法：

1. **SSL证书问题**：首先，请确保你的网站已经安装了有效的SSL证书，并且证书没有过期。Safari通常对SSL证书的要求比较严格，如果证书存在问题，Safari可能会标记网站为不安全。检查证书是否配置正确，是否与你的域名匹配，是否没有过期，并确保SSL证书的链条是完整的。

2. **混合内容问题**：Safari通常不允许在安全连接上加载不安全的混合内容，如HTTP资源。确保你的网站上没有不安全的资源，如不安全的图像、CSS或JavaScript文件。所有资源都应该使用HTTPS。

3. **HSTS（HTTP Strict Transport Security）设置**：如果你的网站使用了HSTS来强制使用HTTPS连接，确保这个设置已正确配置。HSTS设置可让浏览器自动将HTTP请求重定向到HTTPS，提高安全性。

4. **证书链问题**：检查你的SSL证书是否使用了正确的证书链。有时，证书链配置不正确可能导致Safari无法验证证书的有效性。

5. **Safari缓存问题**：有时Safari可能会缓存旧的证书信息，导致显示为不安全。尝试清除Safari浏览器缓存，然后重新加载你的网站。

6. **CSP（内容安全策略）问题**：内容安全策略是一种用于增加网站安全性的机制，但如果配置不正确，也可能导致问题。确保你的CSP设置不会阻止加载你的资源或其他必要的内容。

7. **检查错误信息**：当访问你的网站时，在Safari上查看错误信息或控制台日志，以获取更多关于问题的信息。这可以帮助你更容易地诊断和解决问题。

最重要的是，确保你的网站的所有组件都是安全的，并且你的SSL证书和相关设置都是正确的。如果你不确定如何解决问题，你可以联系你的主机提供商或SSL证书提供商以获取支持。

> Baidu

Safari提示网站不安全是因为要保护您的安全和隐私，网站必须使用强加密才能提供安全的 Web 连接。如果 Safari 提示无法建立安全连接，或网站使用的是弱加密，就会出现这样的提示。要解决此问题，网站管理员应将服务器配置为安全设置

## Safari浏览器整个网页截图

快捷键 `⌘⌥i（win-alt-i）` 打开开发者工具，在`<html`开头的第一行右键选择「捕捉截屏」

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug51.png)

# Win

## [C盘清理步骤](https://blog.csdn.net/qq_43775855/article/details/128374402)

## 隐藏任务栏语言图标

`win-i` 打开设置

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20240114102639400.png)

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20240114102457373.png)

## 查看系统版本号

此电脑--右键-->属性

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug1.png)

## 环境变量

<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug34.png" width=60%/>

用户变量：对该用户起作用，其它用户登录则不起作用

系统变量：对所有用户起作用

`echo %Path% //查看环境变量`

用户环境变量会接在系统环境变量后面

强调：正常对于环境变量，系统会检查**用户**环境变量，之后再检查**系统**环境变量，如果有相同的变量名，并不会将两者的内容合并在一起

path 和 classpath 的作用：

- 运行路径 path 变量记录的是**各个程序所在的路径**，系统根据这个变量的值来查找运行程序（各种命令），使得在运行的时候不用输入全路径名
- 类路径 classpath 环境变量通常用来记录**当前路径和java类库所在的路径**. 在类库中包含java系统所提供的各种软件包，其中包括各个类和接口等

Q：Path变量值变成单行状态，不方便查阅编辑

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug58)

A：`C:\Windows\System32`变量应放在最前面，保存后再打开即可恢复列表状态

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug59)

<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug60" width=70%/>

## Win自动更新问题

Q：系统更新后虚拟机启动蓝屏 卸载更新重启时又自动配置

A：此电脑->右键-管理

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug4.png)

只设置这个没用

<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug5.PNG" width=50%/>

此电脑->右键-属性->高级系统设置

<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug6.PNG" width=50%/>

又设置了这2个 有用 不知道是哪个有用

## [蓝屏PAGE_FAULT_IN_NONPAGED_AREA解决方法](https://jingyan.baidu.com/article/0aa2237516bb1988cc0d64dd.html)

虚拟机同时启动2个就蓝屏，已安装更新又卸载不了，最后用第2个方法解决了

关闭快速启动

1. 任务栏右击电源图标，选择弹出菜单的【电源选项】

   ![](https://exp-picture.cdn.bcebos.com/a007a9b1eef97fbd0bd92807b74133bad2413339.jpg?x-bce-process=image%2Fresize%2Cm_lfit%2Cw_500%2Climit_1%2Fformat%2Cf_jpg%2Fquality%2Cq_80)

2. 在打开的【电源选项】界面左侧点击【选择关闭盖子的功能】或【选择电源按钮的功能】选项

   ![](https://exp-picture.cdn.bcebos.com/c8373cbc7dc5cf6779fac9f28e96b814f5d02639.jpg?x-bce-process=image%2Fresize%2Cm_lfit%2Cw_500%2Climit_1%2Fformat%2Cf_jpg%2Fquality%2Cq_80)

3. 在打开的界面点击【更改当前不可用的设置】，然后取消【启用快速启动】的选中状态，点击【保存修改】，然后重新启动就行了

   ![](https://exp-picture.cdn.bcebos.com/f591ab03c8d246fe1debde37b8bf3bef344f1e39.jpg?x-bce-process=image%2Fresize%2Cm_lfit%2Cw_500%2Climit_1%2Fformat%2Cf_jpg%2Fquality%2Cq_80)

## [Win邮件绑定Google邮箱](https://blog.csdn.net/weixin_47573148/article/details/125828694)

选择最下面**高级设置**，不是**Google**！

 <img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230414021434743.png" style="zoom:67%;" />

| 传入电子邮件服务器             | imap.gmail.com:993:1     |
| ------------------------------ | ------------------------ |
| **传出（SMTP）电子邮件服务器** | **smtp.gmail.com:465:1** |

## Word默认无格式粘贴

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug2.png)

## XShell显示左栏

 <img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug3.jpeg" width=30%/>

## 华为电脑管家 + AI字幕 | 语音输入

[【智慧语音安装教程】非华为电脑 | 华为电脑管家12.0版本 | 智慧语音功能安装教程 | AI字幕 | 语音输入](https://www.bilibili.com/video/BV1YY411p7rE/?spm_id_from=pageDriver&vd_source=dd0980ff81f8ea802fcb0d5ee60569c0)

<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug29.png" width=40%/><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug30.png" width=40%/>

<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug31.png" width=60%/><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug32.png" width=40%/>

退出电脑管家重启 有了

<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug33.png" width=30%/>

## 彻底删除提示“找不到该项目”的目录
新建文本文档 `delete.txt`，粘贴以下代码保存：
```
DEL /F /A /Q \\?\%1
RD /S /Q \\?\%1
```
重命名扩展名为 `.bat`：

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug62.png)

将文件拖入 `delete.bat` 强制删除

## [【此电脑】删除【百度网盘同步空间 / OneDrive / WPS云盘 / 华为云盘】等已经卸载的驱动设备图标](https://www.cnblogs.com/byx1024/p/16793327.html)

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug63.png)

去注册表中删除对应NameSpace，win-r → `regedit`：

```
计算机\HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\Desktop\NameSpace
```

# 网络

## [Win10使用clash开启代理后仍然无法proxy上网的问题](https://www.likecs.com/show-440349.html)

win+r -> `wt` -> `netsh winsock reset` 回车 -> 重启电脑生效 -> 开clash换节点多试几次 ok

## 同一wifi手机连上能上网电脑连上却没网

手机能上网说明wifi没问题,应是电脑配置不当导致

1. 关闭[代理]选项卡

   <img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230912235859895.png"/>

   解决**√**   `127.0.0.1:7890`是代理使用的端口号

2. 重置网络

   管理员身份运行cmd: `netsh winsock reset` 重启电脑生效 或 在设置中重置网络:
   <img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230913000102430.png"/>

其它方法参考 [知乎_同一个Wifi无线网络手机能上但是电脑不能上网的解决方法](https://zhuanlan.zhihu.com/p/538964900)

## 下载出错: 无法连接到代理服务器 127.0.0.1:7890

问题:

<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230730044631579.png" width=60%/>

原因:

<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230730050633987.png" width=70%/>

解决: 更新chrome后解决

<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230730050804331.png" width=60%/>

取消勾选  未解决

<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230730045131441.png" width=60%/>

确认防火墙设置允许IDM从互联网下载文件--将IDM下载软件添加进允许的应用 未解决

<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230730045848410.png"/>

## Snapdrop传输文件时不能连VPN否则连接不上设备

<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230730064748192.png" width=70%/>

同理一些国内app连着VPN也登陆不了/功能受限/加载不出，断开VPN就好了

还有手环之前连了iPad后iPhone就连不上了是以下原因:

<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230730201047087.png"/>

## ChatGPT访问不了

提示: Sorry, you have been blocked

<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230714194345434.png" width=80%/>

无法连接问题:

<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230715003929256.png" width=70%/>

清除浏览器缓存并重启浏览器  / 刷新缓存:

<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230715004256393.png" width=50%/>

## IOS端ChatGPT

注意: VPN要选择全局模式,否则访问不了   虚拟在线号码接收短信服务: https://sms-activate.org/cn 

OpenAI注册ChatGPT: https://openai.com/ PC端注册过则IOS端直接登录就行

<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230726220355315.png"/>

<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230726220418928.png"/>

<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230726221123949.png"/>

<div align="center"><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230728134527715.png" width=70%/></div>

## IP地址显示为其他省份

人在浙江却显示为江苏  IP查询网站：[iP138.com](https://www.ip138.com)

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug42.png)

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug43.png)

可能原因：

- 动态IP所致

  这是由于ISP（互联网服务提供商）的网络结构导致的. 为了节约IP资源，ISP会采用临时随机分配IP方法来提供服务. 当您的ISP更改了您的IP地址，新的IP地址可能会位于另一个省份

- 地理位置数据错误

  IP地址归属地信息通常存储在地理位置数据库中，有时ISP的数据库可能存在错误，导致IP地址与实际地理位置不符

- 虚拟专用网络（VPN）

  如果您使用了VPN服务，您的IP地址会显示为VPN服务器的位置

- 黑客攻击

  如果您的IP地址被黑客攻击或恶意软件感染，黑客可能会在您的设备上安装代理或篡改程序，以便将您的IP地址路由到其他省份

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug44.png)
![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug45.png)
![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug46.png)
![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug47.png)

`192.168.0.1`是一个常见的私有IP地址，通常用作家庭或办公网络中的路由器管理界面的默认IP地址

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug48.png)

# Chrome

## Chrome浏览器截图

<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230926131145110.png" style="zoom: 40%;" />

Mac 快捷键： `⌘⌥i	win-alt-i` 开发者工具 `⌘⇧p	win-shift-p` 运行命令

可以设置语言,要运行命令最好用英文

<div>
<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230926131106343.png" width=40%/><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230926131750715.png" width=50% />
</div>

自定义快捷键不起作用?

## 取消Chrome浏览器自动重置

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230414184833315.png)

## html文档无法通过Chrome浏览器打开

 默认ME浏览器,打开方式中没有Chrome浏览器

 <img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230418022249480.png"/>

win11默认应用设置中没有 `.html` 文件类型

<div>
<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230418014859604.png" width=20% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230418014956916.png" width=30% />
</div>

1. 通过复制路径到Chrome搜索框打开

   <img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230418014739677.png" style="zoom:67%;" />

2. 在Chrome中按 `Ctrl + O` 快捷键浏览文件打开

    <div>
    <img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230418022134854.png" width=60% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230418022155613.png" width=38% />
    </div>   

3. 打开方式选择Chrome
   
   <img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230418022431097.png" style="zoom:75%;" />

## [解决谷歌翻译不能用的方法](https://zhuanlan.zhihu.com/p/571190754?utm_id=0)

换成作者给的第1个ip就行 打开stackoverflow检查🆗了 

<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230418065836126.png" style="zoom:80%;" />

<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230418065801529.png"/>

## 解决网盘下载太慢问题

### 百度网盘加速

使用chrome扩展程序 `篡改猴Beta版` 加载 `百度网盘批量下载` 脚本 + `Motrix` 批量下载工具

[Motrix官网](https://motrix.app)

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug27.png)

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug28.png)

扩展程序安装：[篡改猴测试版](https://chromewebstore.google.com/detail/%E7%AF%A1%E6%94%B9%E7%8C%B4%E6%B5%8B%E8%AF%95%E7%89%88/gcalenpjmijncebpfijmoaglllgpjagf?hl=zh-CN&utm_source=ext_sidebar)  脚本管理器

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug35.png)

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug36.png)

[Greasy Fork](https://greasyfork.org/zh-CN) 脚本网站

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug37.png)

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug38.png)

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug39.png)

和百度网盘、夸克网盘下载速度对比

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug40.png)

若Motrix下载变慢，打开`偏好设置-进阶设置-Tracker服务器`选择有CDN加速的7个服务器，之后点击`保存并应用`即可

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug41.png)

### 各种网盘加速

参考 [网盘直链下载助手_油小猴](https://www.youxiaohou.com/zh-cn/)

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug54.png)

使用chrome扩展程序 `篡改猴Beta版` 加载 `网盘直链下载助手` 脚本 + `Motrix` 批量下载工具

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug55.png)

需要配置相应参数，然后推送到 `Motrix` 中下载

<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug56.png" style="zoom:67%;" />

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug57.png)

# GitHub

## GitHub预览html页面

原页面 

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230915202610254.png)

在地址前加 `raw.githack.com` 预览

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230915202752408.png)

若仓库已发布, 直接在域名仓库名链接后加入对应的html相对路径即可

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230915202956938.png)

## 为什么GitHub有的md文件不能预览

[博客园提问](https://q.cnblogs.com/q/143786/)  [CSDN提问](https://blog.csdn.net/qq_43775855/article/details/132683332?spm=1001.2014.3001.5501)

# IDEA

## 插件

[30多款好用的IDEA插件](https://blog.csdn.net/z_ssyy/article/details/130288021)

CSDN tools  

LeetCode Editor  

Material Theme UI (主题) + Atom Material Icons(突出文件类型图标识别)

Scala  

JetBrains Academy  

Alibaba Java Coding Guidelines

Grep console (自定义控制台打印日志颜色)

## LeetCode插件login with cookie

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug50.png)

## [使用LeetCode插件并调试本地样例](https://blog.csdn.net/HFish24/article/details/105419304/)

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230904193422471.png)

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230904193252220.png)

```java
//Code FileName
[$!{question.frontendQuestionId}]${question.title}
//改为:
P$!{question.frontendQuestionId}_$!velocityTool.camelCaseName(${question.titleSlug})\
    
//Code Template
/**
  * 题目Id：${question.frontendQuestionId}
  * 题目：${question.title}
  * 日期：$!velocityTool.date()
  */
${question.content}
package leetcode.editor.cn;

public class $!velocityTool.camelCaseName(${question.titleSlug}) {
    public static void main(String[] args) {
        Solution solution = new $!velocityTool.camelCaseName(${question.titleSlug})().new Solution();
        System.out.println("Hello world");
    }
    ${question.code}
}
//改为:
${question.content}
package leetcode.editor.cn;
//Java：${question.title}
public class P${question.frontendQuestionId}_$!velocityTool.camelCaseName(${question.titleSlug}){
    public static void main(String[] args) {
       Solution solution = new P$!{question.frontendQuestionId}_$!velocityTool.camelCaseName(${question.titleSlug})****().new Solution();
        // TO TEST
    }
    ${question.code}
}

//Template Constant
${question.title}	题目标题	示例:两数之和
${question.titleSlug}	题目标记	示例:two-sum
${question.frontendQuestionId}	题目编号
${question.content}	题目描述
${question.code}	题目代码
$!velocityTool.camelCaseName(str)	转换字符为大驼峰样式（开头字母大写）
$!velocityTool.smallCamelCaseName(str)	转换字符为小驼峰样式（开头字母小写）
$!velocityTool.snakeCaseName(str)	转换字符为蛇形样式
$!velocityTool.leftPadZeros(str,n)	在字符串的左边填充0，使字符串的长度至少为n
$!velocityTool.date()	获取当前时间
```

## 配置 JDK

File -> Project Structure ->  SDKS 选择

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230904195518436.png)

## 配置 Tomcat

Run -> Edit Configurations

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/bug49.png)

注: 一般开发springring企业级web服务器端项目需要IDEA的企业版，IDEA社区版默认是不能直接创建springboot项目，但IDEA可以通过自定义配置，创建springboot-web项目