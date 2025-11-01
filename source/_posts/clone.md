---
title: 针对大仓库的安全clone命令
date: 2025-11-01 15:19:00
tags: [Git]
index_img: /img/clone.png
banner_img: /img/panda.jpeg
---
## 通用稳定 clone 模板
适合大仓库或网络不稳定的情况，SSH 直接可用：
```shell
# ===============================
# Git 大仓库稳定克隆模板（SSH）
# ===============================

# 1️⃣ 增大传输缓冲区（防止 early EOF）
git config --global http.postBuffer 524288000   # 500MB

# 2️⃣ 关闭压缩，提高下载稳定性
git config --global core.compression 0

# 3️⃣ 克隆仓库（完整历史）
git clone git@github.com:用户名/仓库名.git

# -------------------------------
# 可选：如果想用浅克隆加速首次下载
# git clone --depth 1 git@github.com:用户名/仓库名.git
# cd 仓库名
# git fetch --unshallow  # 拉取完整历史
# -------------------------------

# 4️⃣ 进入仓库
cd 仓库名

# 5️⃣ 查看远程信息，确保使用 SSH
git remote -v
```
🔹 特点：
•	支持大仓库（几百 MB 到几 GB）稳定克隆。
•	SSH 已认证，安全可靠。
•	可选浅克隆加速，适合首次下载慢或网络不稳定。
•	一次配置后，对所有仓库生效，无需重复设置。
## 高级一条命令版稳定 clone 模板
兼顾大仓库、网络不稳定、SSH 认证，同时自动处理浅克隆和全量拉取：
```shell
# ===============================
# 高级稳定克隆大仓库模板（SSH）
# ===============================

# 一条命令实现：
# 1️⃣ 增大缓冲区
# 2️⃣ 关闭压缩
# 3️⃣ 首次浅克隆避免中断
# 4️⃣ 自动拉取完整历史

GIT_HTTP_MAX_REQUEST_BUFFER=524288000 git -c core.compression=0 clone --depth 1 git@github.com:用户名/仓库名.git temp_clone && \
cd temp_clone && \
git fetch --unshallow && \
cd .. && \
mv temp_clone 仓库名

# && → 保证前一个命令成功再执行下一个，避免中途出错。
# \ → 告诉 Shell “命令没结束，继续下一行”，只是换行符号，不影响逻辑

# 写成一行：
GIT_HTTP_MAX_REQUEST_BUFFER=524288000 git -c core.compression=0 clone --depth 1 git@github.com:用户名/仓库名.git temp_clone && cd temp_clone && git fetch --unshallow && cd .. && mv temp_clone 仓库名
```
🔹 功能说明：
1.	缓冲区增大 → GIT_HTTP_MAX_REQUEST_BUFFER=524288000 防止大仓库下载中断。
2.	关闭压缩 → -c core.compression=0 提高下载稳定性。
3.	浅克隆 --depth 1 → 首次下载量小，进度少，更稳定。
4.	自动 fetch --unshallow → 拉取完整历史，无需手动操作。
5.	临时文件夹 temp_clone → 克隆过程中避免与已有同名文件夹冲突，最后重命名为目标仓库名。

这样你以后克隆任何大仓库，只要替换 **用户名/仓库名**，就可以直接用这一条命令，非常稳妥