---
title: Openlist 挂载网盘
date: 2026-07-24 16:57:05
tags:
index_img: /img/openlist.png
banner_img: /img/moon.jpeg
---

Openlist文档 https://doc.oplist.org.cn

## Homebrew安装

```sh
❱❱❱ brew install openlist        
==> Fetching downloads for: openlist
✔︎ Bottle openlist (4.1.9)                            Downloaded   49.2MB/ 49.2MB
==> Pouring openlist-4.1.9.arm64_tahoe.bottle.tar.gz
🍺  /opt/homebrew/Cellar/openlist/4.1.9: 6 files, 135.8MB
==> Running `brew cleanup openlist`...
Disable this behaviour by setting `HOMEBREW_NO_INSTALL_CLEANUP=1`.
Hide these hints with `HOMEBREW_NO_ENV_HINTS=1` (see `man brew`).
==> `brew cleanup` has not been run in the last 30 days, running now...
Disable this behaviour by setting `HOMEBREW_NO_INSTALL_CLEANUP=1`.
Hide these hints with `HOMEBREW_NO_ENV_HINTS=1` (see `man brew`).
Removing: /Users/k/Library/Caches/Homebrew/gmp--6.3.0.arm64_sonoma.bottle.tar.gz... (1MB)
Removing: /Users/k/Library/Caches/Homebrew/unar--1.10.8_2.arm64_sonoma.bottle.tar.gz... (6MB)
Removing: /Users/k/Library/Caches/Homebrew/Cask/rar--7.01.tar.gz... (655.5KB)
Pruned 2 symbolic links from /opt/homebrew
[~] ❱❱❱ openlist server
INFO[2026-01-04 17:37:38] reading config file: /Users/k/data/config.json 
INFO[2026-01-04 17:37:38] config file not exists, creating default config file 
INFO[2026-01-04 17:37:38] load config from env with prefix: OPENLIST_  
INFO[2026-01-04 17:37:38] max buffer limit: 409MB                      
INFO[2026-01-04 17:37:38] mmap threshold: 4MB                          
INFO[2026-01-04 17:37:38] init logrus...                               
Successfully created the admin user and the initial password is: i18zQKsx
start HTTP server @ 0.0.0.0:5244
```

浏览器访问 http://127.0.0.1:5244

![openlist1](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/openlist1.png)

## 开机自启

配置守护进程

```bash
# 确认 OpenList 可执行文件路径
❱❱❱ which openlist
/opt/homebrew/bin/openlist
# 确保工作目录存在
❱❱❱ mkdir -p ~/openlist
# 创建 launchd 配置文件
❱❱❱ vim ~/Library/LaunchAgents/org.openlist.plist
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN"
 "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
  <dict>
    <key>Label</key>
    <string>org.openlist</string>
    <key>ProcessType</key>
    <string>Background</string>
    <key>RunAtLoad</key>
    <true/>
    <key>KeepAlive</key>
    <true/>
    
    <key>WorkingDirectory</key>
    <!--OpenList 运行时的工作路径-->
    <string>/Users/k/openlist</string>

    <key>ProgramArguments</key>
    <array>
    	<!--OpenList 实际路径-->
      <string>/opt/homebrew/bin/openlist</string>
      <string>server</string>
    </array>

		<!--日志排错:端口占用、权限、路径问题-->
    <key>StandardOutPath</key>
    <string>/tmp/openlist.log</string>
    <key>StandardErrorPath</key>
    <string>/tmp/openlist.err</string>
  </dict>
</plist>
# 加载/开启/关闭/卸载配置
❱❱❱ launchctl load/start/stop/unload ~/Library/LaunchAgents/org.openlist.plist
# 注意 config 位置
[~/openlist] ❱❱❱ openlist server                
INFO[2026-01-05 00:51:49] reading config file: /Users/k/openlist/data/config.json 
```

**OpenList 本地文件机制**

```bash
WorkingDirectory/data
├── config.json # 程序运行配置（端口、站点设置）
├── data.db			# 核心数据库核心数据库（挂载网盘、用户、任务等）
├── data.db-shm # SQLite 共享内存索引（WAL 配套）
├── data.db-wal # SQLite 写前日志（运行时最新数据）
├── log					# 运行日志（排错用，可删）
└── temp				# 临时文件（下载/代理中转，可删）
```

这是 **OpenList + SQLite（WAL 模式）** 的典型结构，data.db + data.db-wal + data.db-shm **必须成套**

- **配置和数据都存在** **WorkingDirectory/data**

- 如果 data 不存在 → 自动创建

- 删除原始 ~/data → 数据丢失(包括在 Web 端挂载的网盘信息、用户密码)

不要直接删旧目录，应该 **迁移数据** 到新的 WorkingDirectory，备份/迁移前先停止 OpenList：
```bash
mv ~/data ~/openlist/
```
这样 `~/openlist/data` 就包含原来的配置，launchd 启动后可以直接使用

## 添加存储

### 阿里云盘

选择“阿里云盘Open” 填入得到的刷新令牌

![openlist2](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/openlist2.png)

### 百度网盘

选择“百度网盘” 获取Token(同上) n个账号刷新Token再获取

下载文件报错，因为百度网盘下载>20M需要修改UA➡️后台开启代理

![openlist3](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/openlist3.png)

![openlist4](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/openlist4.png)

### 夸克网盘 一刻相册

选择“夸克” 填入Cookie：`f12 / win-alt-i`打开调试-网络 刷新后找到`sort`开头的`Cookie`

一刻相册获取Cookie同上

![openlist5](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/openlist5.png)

### 迅雷云盘

选择“迅雷” 填入账号(手机号)密码和短信验证后得到的`creditkey`

![openlist6](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/openlist6.png)

![openlist7](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/openlist7.png)

![openlist8](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/openlist8.png)

### 中国移动云盘

启用 `Web 代理`  填入账号(手机号)密码和`Authorization`

![openlist9](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/openlist9.png)

获取`Authorization`  以下方法都行：

![openlist10](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/openlist10.png)

### 配置完成✅

![openlist11](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/openlist11.png)

可在本地数据库文件查看已挂载的网盘信息 (`SELECT id, mount_path, driver, remark, status FROM x_storages;`)

```sh
[~/openlist/data] ❱❱❱ ls
config.json data.db     data.db-shm data.db-wal log         temp
[~/openlist/data] ❱❱❱ sqlite3 data.db
SQLite version 3.51.0 2025-06-12 13:14:41
Enter ".help" for usage hints.
sqlite> .tables
x_meta             x_setting_items    x_ssh_public_keys  x_task_items     
x_search_nodes     x_sharing_dbs      x_storages         x_users          
sqlite> .schema x_storages 
CREATE TABLE `x_storages` (`id` integer PRIMARY KEY AUTOINCREMENT,`mount_path` text,`order` integer,`driver` text,`cache_expiration` integer,`custom_cache_policies` text,`status` text,`addition` text,`remark` text,`modified` datetime,`disabled` numeric,`disable_index` numeric,`enable_sign` numeric,`order_by` text,`order_direction` text,`extract_folder` text,`web_proxy` numeric,`webdav_policy` text,`proxy_range` numeric,`down_proxy_url` text,`disable_proxy_sign` numeric,CONSTRAINT `uni_x_storages_mount_path` UNIQUE (`mount_path`));
sqlite> SELECT
   ...>   id,					# 字段说明:
   ...>   mount_path, # Web上的挂载路径
   ...>   driver,			# 网盘类型
   ...>   remark,			# =后台备注
   ...>   status			# work=正常  error=异常(token失效/掉线) init=未初始化 disabled=被禁用 
   ...> FROM x_storages;
1|/Aliyun|AliyundriveOpen||work
2|/Baidu19|BaiduNetdisk||work
3|/Baidu11|BaiduNetdisk||work
4|/Quark16|Quark||work
5|/Thunder|Thunder||work
6|/Quark|Quark||work
9|/中国移动云盘|139Yun||work
10|/一刻相册11|BaiduPhoto||work
11|/一刻相册19|BaiduPhoto||work
sqlite> .exit
```