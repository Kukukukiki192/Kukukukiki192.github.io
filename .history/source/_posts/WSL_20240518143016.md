---
title: WSL（Windows Subsystem for Linux）
date: 2024-02-04 15:35:16
tags: [WSL, Linux]
index_img: /img/wsl.png
banner_img: /img/MC_castle1.jpg
---
参考：

[适用于 Linux 的 Windows 子系统文档](https://docs.microsoft.com/zh-cn/windows/wsl/)

[为 win10 打造原生Linux 终端：使用WSL作为Windows下的主力开发工具](https://juejin.cn/post/6844904064535248909#heading-0)

# 激活 WSL 功能

<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20211006015248161.png" width=60%/>

重启电脑

# 安装 Ubuntu

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20211006112559439.png)

第一次启动需要几分钟

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20211006204709328.png)

# 安装 Windows Terminal

安装 Windows Terminal，是因为在配置 oh-my-zsh 主题的时候，要进行一些操作，比如修改 WSL 字体、修改背景透明度、设置背景图片、设置默认打开路径等，Terminal 的配置文件让这些操作都变得十分简单

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20211006230745423.png)

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20211006225304825.png)

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20211006225330181.png)

[配置终端](https://docs.microsoft.com/zh-cn/windows/terminal/customize-settings/profile-general)  [将 Git-bash 置入 Windows Terminal](https://segmentfault.com/a/1190000020208609)

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20211007001807107.png)

***

已更新的设置：

<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20240204155111686.png" width=65%/>

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20240204154424890.png)

# 美化终端
> [ohmyzsh官网](https://github.com/ohmyzsh/ohmyzsh) 

安装和使用 `oh-my-zsh` 框架来美化终端：
```bash
# 1.安装 zsh
sudo apt update
sudo apt install zsh
# 2.安装 Oh My Zsh：用 curl 或 wget
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
sh -c "$(wget https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"
# 3.切换到 zsh
chsh -s $(which zsh)
```
![oh_my_zsh](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/oh_my_zsh.png)

更多配置参考 [macOS开发环境配置_美化终端](http://kk1024.cool/2024/02/03/MacDE%E9%85%8D%E7%BD%AE/#%E7%BE%8E%E5%8C%96%E7%BB%88%E7%AB%AF)

激活插件后效果：

`git`

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20240511143318657.png)

`web_search`

![web_search](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/web_search.gif)

自动补全、语法高亮、提示别名

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20240511155724103.png)
