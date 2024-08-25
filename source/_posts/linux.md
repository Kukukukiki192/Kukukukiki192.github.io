---
title: Linux
date: 2023-02-04 18:14:31
tags: [Linux]
index_img: /img/linux.png
banner_img: /img/dragon3.jpg
---
[参考笔记](https://blog.csdn.net/weixin_44262126/article/details/108217320)  [《Linux就该这么学》在线书籍 ](https://www.linuxprobe.com/) [Linux命令大全(手册)](https://www.linuxcool.com/) [Linux-Tutorial](https://github.com/judasn/Linux-Tutorial)

# VM CentOS

> 环境  `VMWare 16.2`   `CentOS 8.5`

## 创建虚拟机

 <div><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204183333348.png"   width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204183418771.png"   width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204183436550.png"   width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204183455168.png"   width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204183707509.png"   width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204183916666.png"   width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204183935071.png"   width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204183947796.png"   width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204184008316.png"   width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204184032630.png"   width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204184047771.png"   width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204184214195.png"   width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204184231661-1675507934147-1.png"   width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204184707182.png" alt=" 自定义硬件 中引用iso后点完成"  width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204184444846.png" alt="引用iso镜像文件前确保 已启用虚拟化"  width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204184604106-1675511278167-9.png" alt="引用iso镜像文件"  width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204184748060.png" alt="或点完成后再去 虚拟机设置 中引用iso"  width=50% /></div>

## 安装CentOS

<div><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204193015657.png"   width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204185449393.png"   width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204193554030.png"   width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204185525202.png"   width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204190158845.png"   width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204190335581.png"   width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204190826378.png"   width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204191008721.png"   width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204191129347-1675510451740-5.png"   width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204192122125.png"   width=50% /></div>

KDUMP-实际服务器中需启用，但自己做测试可以先禁用以节省资源

> 安装界面显示不全，因为屏幕分辨率未被正确识别，要关闭虚拟机修改显示器设置，选择本机真实屏幕分辨率重启安装（重启后要重新走以上步骤）
> <div><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204192720597.png"   width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204192717600.png"   width=50% /></div>

<div><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204193832775.png"   width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204194018979.png"   width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204194303003.png"   width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204194519385.png"   width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204195851209.png"   width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204195928424.png"   width=50%  /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204195937488.png"   width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204195947460.png" alt="结束配置并重启虚拟机"   width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204200013512.png" alt="登录"  width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204200527438.png" alt="检查网络"  width=50% /></div>

***

进入 `Centos8.5` 系统后，发现桌面上没有任何图标而且右键没有终端/新建等操作，即使使用终端新建一些文件，也无法在桌面上显示

`Centos7`默认为`X11`桌面版本，但是`Centos8`默认为`Wayland`，此时需要更换桌面版本，然后就能正常显示了

<div><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204202259819.png"   width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230206201402473.png"   width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230206201802954-1675686295564-1.png"   width=50%/><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204204210896.png" alt="配置打开终端快捷键"  width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204205808263.png" alt="计算机 位于 其他位置"  width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230204205827017.png"   width=50% /></div>

添加共享文件夹	Windows `D:\vm\share\`	Linux  `/mnt/hgfs/share`

<div><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230206193811434.png"   width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230206202721065.png"   width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230206202222959.png" alt="在桌面创建共享文件夹快捷方式"  width=50% /></div>

设置无密登录

<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230213125408412.png" alt="image-20230213125408412" style="zoom: 67%;" />

## 远程登录 Linux 系统

测试 Windows 和 Linux 是否相通：

```shell
ifconfig #network interfaces configuring网络接口配置 功能描述：显示所有网络接口的配置信息
ping ip地址/目的主机 #功能描述：测试当前服务器是否可以连接目的主机
```

<div><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230206204532820.png" alt="在 Linux 下 ifconfig 查看当前网络 IP"  width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230206204524902.png" alt="在 Windows 下 ping Linux 的 IP 地址"  width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230206204955972.png" alt="设置-网络-有线"  width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230206204948425.png" alt="设置中查看 Linux 的 IP 地址"  width=50% /></div>

XShell 连接虚拟机：

<div><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230206205936968.png"/><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230206210938410.png"/><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230206211020893.png"/></div>

注意（Linux 默认开启 SSHD 服务）：

<div><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/1625500041853-a39edcc8-6467-4306-a29c-7e55fc85d01b.png"/>
    <img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230206212458911.png"/></div>

# Linux 世界里 一切皆文件

文件颜色：

<font color=green>绿色		可执行文件，可执行的程序</font>

<font color=red>红色		压缩文件或者包文件</font>

<font color=blue>蓝色		目录</font>

黑底白字/白底黑字		一般性文件，如文本文件，配置文件，源码文件等

<font color=lightblue>浅蓝色		链接文件，主要是使用ln命令建立的文件</font>

<font color=pink>红色闪烁		链接的文件有问题</font>

<font color=orange>黄色		设备文件</font>

<font color=gray>灰色		其他文件</font>

文件属性：

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/1625499727651-1f3f5de9-6a84-4d52-b014-2bfba7ed22ac.png)

环境变量：

配置全局环境变量，用 `root` 用户权限写入 `sudo vim /etc/profile.d/my_env.sh`，使脚本生效 `source /etc/profile`

# VIM

[VIM Adventures玩游戏练VIM](https://zhuanlan.zhihu.com/p/165254171)

**vi**(文本编辑器)--[增强版]-->**vim**(具有程序编辑能力)

<div><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230211172143688-1683698172248-1.png" width=52% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230211164529648.png" width=48% /></div>

```shell
:set nu		#显示行号
:set nonu	#取消行号
:noh		#取消高亮
:s/old/new		#替换当前行匹配到的第1个old为new
:s/old/new/g	#替换当前行匹配到的所有old为new
:%s/old/new		#替换文档中匹配到的第1个old为new
:%s/old/new/g	#替换文档中匹配到的所有old为new
/[关键字]  #--[enter]--> 查找 --[n]--> 查找next
```

# 网络配置

## 网络连接的3种形式

<div><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/1625496025387-c7b6019a-8b3c-4d6a-95f3-a8321d7d2aff.png" width=30% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/1625496806099-b615c090-c0fc-4e92-aff1-2e84e5595cf2.png"/><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230213131007090.png" width=70%/></div>

## 查看 Windows 网络配置

- 从设置进入(或通过WiFi图标查看)：设置-网络和Internet-状态-更改适配器选项

  <div><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230211170009576-1676112153710-3-1683698429922-9.png" width=20% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230211165836331.png" width=40% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230211190256705.png" alt="Windows网络连接" width=40% /></div>

- 或从控制面板进入：控制面板-网络和Internet-查看网络状态和任务-更改适配器设置（界面同上）

  <div><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230211170407366-1683698500796-15.png" width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230211170346975.png" width=50% /></div>

- <img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230211170726981.png" alt="在 Windows下 ipconfig 查看网络配置" width=50% />

## 查看 Linux 网络 IP 和网关

<div><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230211190855332.png" width=60% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230206204532820.png" alt="在 Linux 下 ifconfig 查看当前网络 IP"  width=40% /></div>

## Linux 网络环境配置

- 默认自动获取：每次获取的ip可能不同，不适合服务器（ip是固定的）

  <div><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230213124821145.png" width=50%/><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230211185454466-1683698341971-6.png" width=50% /></div>

- 通过修改配置文件指定固定ip（root用户）：

  ```shell
  #修改网络配置文件 当前局域网在Linux中的设备名是ens160(很多是ens33)
  vim /etc/sysconfig/network-scripts/ifcfg-eth160
  
  #修改内容
  #IP地址(主机名是hadoop100,最后一个网段改为100好记)
  IPADDR=192.168.1.100   
  #网关  
  GATEWAY=192.168.1.2      
  #域名解析器(可添加多个 dns和网关保持一致)
  DNS1=192.168.1.2
  #子网掩码默认255.255.255.0
  
  #重启网络 若报错reboot重启虚拟机
  service network restart
  systemctl restart network	#centos7以后新增
  
  #修改主机名和主机映射文件 重启生效
  hostname	#查看当前服务器主机名
  vim /etc/hostname	#当前服务器主机名
  vim /etc/sysconfig/network	#HOSTNAME属性修改主机名(我的该文件没有内容)
  hostnamectl	#显示主机名和一些系统相关的信息(CentOS7及以上版本才增加的命令 ctl指control)
  hostnamectl set-hostname 主机名	#永久修改主机名且无需重启系统
  vim /etc/hosts	#主机映射文件
  ```

  `C:\Windows\System32\drivers\etc\HOSTS`--Windows主机映射文件 (拷贝出来修改后再替换原文件) 若在该文件下写入 `www.sharm.com 百度`，则在浏览器搜索百度时会跳转到写入的这个网站中，这叫[域名劫持](https://baike.baidu.com/item/%E5%9F%9F%E5%90%8D%E5%8A%AB%E6%8C%81/7657893?fromtitle=DNS%E5%8A%AB%E6%8C%81&fromid=6739044&fr=aladdin)

  <div><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230213142813539.png" alt="修改配置文件指定固定ip" width=80% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230213144341959.png" alt="检查修改后的ip" width=70% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230213150148564.png" alt="Windows测试连接Linux修改后的ip地址" width=30% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230213150751755.png" width=70% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230213153116873.png" alt="查看和修改主机名" width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230213151952620.png" alt="/etc/hosts主机映射文件" width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230213145319818.png" alt=" Windows主机映射文件" width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230213153859396.png" alt="直接ping主机名" width=50% /></div>

修改XShell设置：

<div><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230213155622655.png" width=52% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230213155539451.png" width=38% /></div>

修改Xftp设置解决文件名中文乱码问题：

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230213160207227.png)

# 系统管理

## 服务管理

**进程 process**：一个正在执行的程序或命令

**服务 service**：启动后一直存在、常驻内存的进程（运行在后台，监听某个端口，等待其它程序的请求--由守护进程daemon守护系统服务，d结尾表示这是守护进程）

<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230217145806826.png"/>

```shell
service 服务名 start|stop|restart|reload|status #CentOS7.0前(7.0后兼容) 查看服务：/etc/init.d/服务名称
systemctl start|stop|restart|reload|status 服务名 #CentOS7.0后 查看服务：/usr/lib/systemd/system/服务名称
```

`setup` 查看服务名：在vm中(而不是xshell)使用该命令选择 `系统服务` 回车

<div><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230217183336462-1683700479118-19.png" width=30% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230217183340674.png" width=40% /></div>

常用服务：

网络服务 `network` (CentOS7默认使用的网络服务是NetworkManager) [报错记录](https://blog.csdn.net/qq_43775855/article/details/129088280?spm=1001.2014.3001.5502)

防火墙 `iptables`

关闭或启用防火墙后立即生效，可通过telnet在Windows下测试：

[telnet 查看某个端口是否可访问](https://cloud.tencent.com/developer/article/2113234)

`telnet ip [端口]` 利用telnet指令检查Linux的某个端口是否在运行

<div><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230220125354284.png" width=35% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230220125324089.png" width=30% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230220125411803.png" width=25% /></div>

`service/systemctl` 方式只是临时生效，当重启系统后，还是回归以前对服务的设置，设置永久生效要使用 `chkconfig` 指令

## 系统运行级别

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230217174629462.png)

```shell
multi-user.target	#=原运行级别3 多用户有网 无图形界面
graphical.target	#=原运行级别5 多用户有网 有图形界面
systemctl get-default #查看当前运行级别
systemctl set-default TARGET.target #修改当前运行级别 TARGET取multi-user或graphical
```

centos7以前查看默认运行级别在 `/etc/inittab`

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230217184209047.png)

`ctrl+shft+f2 f1`

## 配置服务开机启动 关闭防火墙

chkconfig设置服务自启动/关闭需reboot重启机器生效

查看当前系统中使用chkconfig工具的服务：

```shell
[root@hadoop100 ~]# chkconfig --list

注：该输出结果只显示 SysV 服务，并不包含
原生 systemd 服务。SysV 配置数据
可能被原生 systemd 配置覆盖。 

      要列出 systemd 服务，请执行 'systemctl list-unit-files'。
      查看在具体 target 启用的服务请执行
      'systemctl list-dependencies [target]'。

network        	0:关	1:关	2:关	3:关	4:关	5:关	6:关
```

centos6及更早版本使用的服务管理机制叫SysV，centos7使用的服务管理机制叫systemd

centos6的服务管理进程为init，centos7中的服务管理进程为systemd

network服务脚本的存放位置：

```shell
[root@hadoop100 ~]# ls /etc/init.d/
functions  network  README
```

systemd是centos7的服务管理机制，列出systemd中的service：

```shell
systemctl list-units --all --type=service
```

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230220123111428.png)

`LOAD`：是否load	`ACTIVE`：是否active	`SUB`：是否running	`DESCRIPTION`：描述信息

不加 `–all` 则不会列出 inactive（未激活状态）的 service

```shell
systemctl list-unit-files #显示的内容不仅是service还有target、socket
```

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230220123736381.png)



## [关机 重启](https://www.linuxcool.com/shutdown)

```shell
sync	#内存数据写入磁盘防止数据丢失 <-h/r前先执行
halt	#立刻关机
reboot	#立刻重启
shutdown -h now	#立刻关机
shutdown -h 1	#1min后关机
shutdown -r now	#立刻重启
shutdown -r 2	#2min后重启
```







# 常用命令

## 帮助指令

man ls	(ls是外部命令->其他独立的程序 和shell同级)

help cd	(只能显示shell**内置**命令的帮助信息)

百度更直接

区分内置命令和外部命令-**which / type**

<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/1626336467891-2ae32ca2-3c8f-4923-b3d9-72c27a419738.png" widt=20% />

1. 如果是内置命令 [shell内置命令](http://c.biancheng.net/view/1136.html)

```shell
[root@VM_0_8_centos ~]# type cd  
cd is a shell builtin 
```

builtin的英文翻译就是内置命令

2. 如果是自己写的shell脚本

```shell
[root@VM_0_8_centos ask]# type /ask/test.sh  
/ask/test.sh is /ask/test.sh 
```

自己写的shell脚本是外部命令，它的位置是/ask/test.sh

3. 常见的find命令

```shell
[root@VM_0_8_centos ask]# type find 
find is /usr/bin/find 
```

find是一个外部命令，它的位置是/usr/bin/find

注:

<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/1626337648972-8797a43f-54ff-4427-91f8-b3c707e07869.png" widt=20% />

sudo cd root 并没有切换到root目录

sudo 是一种**程序**，用于提升用户的权限

shell是一个**命令解析器**，sudo cd是错误的，因为cd是shell内置的，不是系统里面的

sudo可以运行系统带的命令，但无法运行系统一个软件中的命令

所以这里要切换到root目录，只能先切换到root用户

常见shell内置命令

```shell
source	#在当前bash环境下读取并执行指定的命令
echo	#输出指定的字符串或者变量
type	#显示指定命令的类型
env		#显示系统中已存在的环境变量
exec	#调用并执行指定的命令
kill	#删除执行中的程序或工作
alias	#用来设置指令的别名
unalias	#用来删除指令的别名
exit	#退出当前的shell
jobs	#显示linux的任务列表和状态
history	#显示历史命令
logout	#退出当前登录的shell
export	#设置或者显示当前登录的shell
cd		#切换工作目录
```



内置命令

外部命令

type [cmd]

… 是 shell 

help [shell内置命令]

[外部命令] –help

man [cmd] 最全

man -f [内置命令]



tail  -f  文件	#实时追踪该文档的所有更新



\> 输出重定向（覆盖） >> 追加

ls -l >文件		（功能描述：列表的内容写入文件a.txt中（**覆盖写**））

ls -al >>文件		（功能描述：列表的内容**追加**到文件aa.txt的末尾）

cat 文件1 > 文件2	（功能描述：将文件1的内容覆盖到文件2）

echo “内容” >> 文件



ln -s xiyou/dssz/ ./dssz	#创建软连接

cd -P dssz/	#进入软连接实际物理路径

删除软链接： rm -rf 软链接名，而不是rm -rf 软链接名/



date +%Y%m%d	#显示当前时间年月日

date "+%Y-%m-%d %H:%M:%S"	#显示当前时间年月日时分秒

cal [年份]	#日历

## 用户管理

用户登录->自动(默认)进入家目录(/home/k即~)	一个用户不能进入其它用户目录

#### su切换用户

```shell
[root@hadoop100 ~]# su k	#只能获得用户的执行权限,不能获得环境变量
[k@hadoop100 root]$ su
密码：
[root@hadoop100 ~]# su - k	#获得该用户的执行权限及环境变量
[k@hadoop100 ~]$ su -	#普通用户->系统管理员
密码：
[root@hadoop100 ~]# exit	#返回原来的用户/断开连接
注销
```

注销用户 / 退出远程登录：

<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/1625561513595-0632da31-89e6-4d4d-a130-4ad3ac03fdb5-1676614829778-1.png" width=50% />

注销指令在 **图形运行级别**(级别5) 无效，在 控制台命令行模式(级别3) 下有效：

<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/1625561385041-f52fefa7-4536-4caa-8696-7c06733b834c-1676614829778-3.png"/>

#### sudo用root权限执行操作

添加用户k具有root权限，配置成采用sudo命令时无需输入密码

```shell
vim /etc/sudoers
## Allow root to run any commands anywhere 
root    ALL=(ALL)       ALL
k       ALL=(ALL)     NOPASSWD:ALL
```

#### 查询用户信息

<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230213181513380.png"/>

#### 用户组

<div><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/1625563766982-4784003c-10b7-4421-87f2-53270734e3b1-1676283414442-7.png" alt="新用户指定组/修改用户的组" width=40% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/1625563899891-bfa78df1-be00-4376-b6cd-c6ebec63e36b.png" alt="组无用户才能删" width=40%/></div>

#### 用户和组相关文件

**/etc/passwd**文件： 用户配置，记录用户的各种信息   口令：用户加密密码，加密后的密码保存在/etc/shadow文件

<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230213182612000.png"/>

**/etc/shadow**文件： 口令配置

<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230213183107600.png"/>

**/etc/group**文件： 组配置，记录Linux包含的组的信息

<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230213183351833.png"/>

​	

