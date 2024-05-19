---
title: 常见 Linux 命令及其在 Windows 中的替代方案
date: 2024-05-19 15:00:15
tags: [Linux, CMD, PowerShell]
index_img: /img/terminal.png
banner_img: /img/terminal1.png
---
❗在 Windows 环境中，特别是 CMD（Command Prompt）和 PowerShell 中，有许多 Linux 命令是不能直接使用的

- **Shell 环境**：Linux 使用的是各种 shell 环境，如 bash、zsh 等. Windows CMD 和 PowerShell 在功能和脚本语言上与这些 shell 环境有很大差异
- **脚本编写**：PowerShell 支持更强大的脚本编写和自动化功能，语法类似于编程语言. 而 CMD 的批处理脚本功能相对有限
- **工具链**：在 Windows 上，可以使用 Windows Subsystem for Linux (WSL) 来运行 Linux 命令. 这提供了一个真正的 Linux 兼容层，可以运行大多数 Linux 命令和工具

以下是一些常见的 Linux 命令及其在 Windows 中的替代方案或等效命令：

| Linux 命令 | 描述                 | CMD 替代                                      | PowerShell 替代                      |
| ---------- | -------------------- | --------------------------------------------- | ------------------------------------ |
| `which`    | 查找命令的路径       | `where`                                       | `& 'C:\Windows\System32\where.exe'`  |
| `ls`       | 列出目录内容         | `dir`                                         | `Get-ChildItem` 或 `ls`              |
| `cp`       | 复制文件或目录       | `copy` 或 `xcopy`                             | `Copy-Item`                          |
| `mv`       | 移动文件或目录       | `move`                                        | `Move-Item`                          |
| `rm`       | 删除文件             | `del` 或 `erase`                              | `Remove-Item`                        |
| `touch`    | 创建空文件           | `type NUL > <file>`                           | `New-Item -ItemType File`            |
| `cat`      | 显示文件内容         | `type`                                        | `Get-Content` 或 `cat`               |
| `grep`     | 搜索文本             | `findstr`                                     | `Select-String`                      |
| `ps`       | 显示进程列表         | `tasklist`                                    | `Get-Process`                        |
| `kill`     | 终止进程             | `taskkill /PID <pid> /F`                      | `Stop-Process -Id <pid>`             |
| `chmod`    | 更改文件权限         | `icacls` 或 `attrib`                          | `icacls` 或 `attrib`                 |
| `chown`    | 更改文件所有者       | `icacls`                                      | `icacls`                             |
| `df`       | 显示磁盘使用情况     | `wmic logicaldisk get size,freespace,caption` | `Get-PSDrive -PSProvider FileSystem` |
| `du`       | 显示目录空间使用情况 | 无直接等效命令                                | `Get-ChildItem <path> -Recurse       |
| `man`      | 显示命令手册         | `<command> /?`                                | `Get-Help <command>`                 |
| `nano/vi`  | 文本编辑器           | `notepad <file>`                              | `notepad <file>` 或其他文本编辑器    |

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/terminal.png)

`which` 和 `where` 命令都用于**查找可执行文件的路径**，但它们在不同的操作系统和环境中有不同的行为：

- **操作系统**：`which` 主要用于类 Unix 系统（如 Linux、Unix、macOS），而 `where` 主要用于 Windows 系统
- **输出格式**：`which` 输出匹配的命令的完整路径，而 `where` 输出所有匹配的命令的路径
- **功能**：虽然功能类似，但 `where` 的输出通常更详细，并且可以显示多个匹配项