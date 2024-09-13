---
title: Windows快捷键
date: 2024-02-03 19:36:24
tags: [快捷键, CMD, IDEA, VSCode, Notepad++, XShell]
index_img: /img/win.png
banner_img: /img/virus.JPG
---
# [Windows 的键盘快捷方式](https://support.microsoft.com/zh-cn/windows/windows-%E7%9A%84%E9%94%AE%E7%9B%98%E5%BF%AB%E6%8D%B7%E6%96%B9%E5%BC%8F-dcc61a57-8ff0-cffe-9796-cb9706c75eec)

**快捷键**

| 键盘                   |                                      |
| :--------------------- | ------------------------------------ |
| `Ctrl-Shift-E`         | 打开emoji符号面板                    |
| `Shift`                | 中/英切换                            |
| `Ctrl-.`               | 中/英标点切换                        |
| `Shift-Space`          | 全/半角切换                          |
| **文件**               |                                      |
| `Ctrl-S`               | 保存                                 |
| `Ctrl-W` / `Alt-F4`    | 关闭                                 |
| `Ctrl-Y`               | 恢复                                 |
| `Ctrl-N`               | 在所选项上新建空白窗口               |
| **电脑**               |                                      |
| `Win-L`                | 锁屏                                 |
| `Win-D`                | 返回桌面                             |
| `Win-Z`                | 分隔窗口                             |
| `Win-R`                | 打开运行                             |
| `Win-E`                | 打开此电脑                           |
| `Win-I`                | 打开设置                             |
| `Win-X`                | 打开快捷菜单(开始菜单右键)           |
| `Win-W`                | 打开小组件                           |
| `Alt-Q`                | 智慧搜索                             |
| `Alt-Tab`              | 切换应用(触摸板==三指左右划不挪开==) |
| `Win-Tab`              | 进入虚拟桌面(触摸板==三指上划==)     |
| `Ctrl-Win-left/right`  | 切换虚拟桌面(触摸板==四指左右划==)   |
| `Ctrl-Win-D`           | 添加虚拟桌面                         |
| `Ctrl-Alt-Delete`      | 调出安全窗口(→任务管理器)            |
| `Ctrl-Esc` / `Win`     | 开始菜单                             |
| `Insert`               | 光标 `|` ↔ `_`                       |
| **浏览器**             |                                      |
| `F12` / `Ctrl-Shift-I` | 打开开发者工具                       |
| `Ctrl-Shift-P`         | 开发者工具中弹出搜索框               |
| `F5`                   | 刷新当前窗口                         |
| `Tab`                  | 改变焦点 回到页首                    |
| `M`                    | 看视频时静音                         |

**cmd 命令行**

```sh
control #打开控制面板
ipconfig [/all显示更详细信息] #查看和配置网络接口信息(Linux: ifconfig 新版命令ip addr show)
ipconfig /flushdns #刷新缓存
netsh winsock reset #重置网络
```

**win-r 运行**

| 输入                     | 启动程序                                               |
| ------------------------ | ------------------------------------------------------ |
| `wt`                     | Windows Terminal                                       |
| `cmd`                    | Command Prompt                                         |
| `powershell`             | PowerShell                                             |
| `control`                | 控制面板                                               |
| `taskmgr`                | 任务管理器                                             |
| `regedit`                | 注册表                                                 |
| `calc`                   | 计算器                                                 |
| `notepad`                | 记事本                                                 |
| `write`                  | 写字板                                                 |
| `mspaint`                | Microsoft Paint 画图工具                               |
| `services.msc`           | 服务                                                   |
| `compmgmt.msc`           | 计算机管理                                             |
| `devmgmt.msc`            | 设备管理器                                             |
| `gpedit.msc`             | 组策略                                                 |
| `sysdm.cpl`              | 系统属性（高级-环境变量）                              |
| `inetcpl.cpl`            | Internet属性                                           |
| `appwiz.cpl`             | 程序和功能（卸载或更改程序）                           |
| `Firewall.cpl`           | 防火墙                                                 |
| `osk`                    | 屏幕键盘                                               |
| `winver`                 | 显示Windows版本和构建信息                              |
| `mstsc`                  | 远程桌面连接                                           |
| `msconfig`               | 系统配置实用程序（配置系统启动项和服务）               |
| `msinfo32`               | 系统信息实用程序（显示有关计算机硬件和软件的详细信息） |
| `dxdiag`                 | DirectX诊断工具（检查图形和音频驱动程序）              |
| `control userpasswords2` | 用户帐户窗口                                           |
| `wuapp`                  | win更新                                                |
| `logoff`                 | 注销命令                                               |
| `%temp%`                 | 临时文件夹                                             |
| `shutdown -s -t 60`      | 60s后自动关机                                          |
| `shutdown -a`            | 取消定时关机                                           |

# 开发工具

| Notepad++          |           |
| :------------------ | --------- |
| `Ctrl-Shift-Alt-B` | xml格式化 |

| VSCode     | 格式化代码       |
| :---------- | :---------------- |
| On Windows | `Shift-Alt-F`    |
| On Mac     | `Shift-Option-F` |
| On Ubuntu  | `Ctrl-Shift-I`   |

| XShell          |                |
| :--------------- | -------------- |
| `Ctrl-鼠标滚轮` | 页面放大缩小   |
| `Ctrl-L`        | clean页面      |
| `Shift-Insert`  | 黏贴到终端     |
| `ALT-E`         | 唤出顶部菜单栏 |

# IDEA

| `Alt-Shift-↑/↓/←/→`      | 选中多列、多行        |
| :----------------------- | :--------------------- |
| `Ctrl-K`                 | commit ✔              |
| `Ctrl-Shift-K`           | push ↗                |
| `Alt-9`                  | 预览项目提交历史      |
| `Ctrl-W`                 | expand code selection |
| `Ctrl-/`                 | 单行注释              |
| `Ctrl-Shift-/`           | 多行注释              |
| `Alt-1`                  | 打开工具窗口          |
| `Alt-~`                  | 打开Git命令窗口       |
| `Ctrl-滚轮 / 触摸屏缩放` | 调整字体大小          |
| `Ctrl-F`                 | 本页 查找             |
| `Ctrl-Shift-F`           | 全局 查找             |
| `Ctrl-R`                 | 本页 查找替换         |
| `Ctrl-Shift-R`           | 全局 查找替换         |
| `Ctrl-Alt-S`             | #打开设置             |
| `Ctrl-Alt-L`             | 格式化                |
| `Ctrl-Alt-F`             | 局部变量提升成属性    |
| `Ctrl-Alt-0`         | 更换bgImage(自定义)   |
| `Ctrl-Shift-A`           | 设置bgImage等属性     |
| `Shift-Tab`              | 整体左移              |
| 按2次 `Shift`            | Search Everywhere     |
| `Ctrl-N`                 | 搜索类                |
| `Ctrl-Q`                 | 预览类文档            |
| `Ctrl-Alt-Shift-N`       | 搜索方法和全局变量    |
| `Ctrl-Shift-N`           | 搜索文件              |

快捷键更换背景图![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230904183436134.png)

设置鼠标滚轮缩放字体效果
![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230904183456853.png)
![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230704000238860.png)
![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230704000309591.png)
![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230704000315880.png)
![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230704000321832.png)