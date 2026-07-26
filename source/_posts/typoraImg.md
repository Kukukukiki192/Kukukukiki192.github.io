---
title: Typora + PicGO-Core(cmd安装方式) + Github 实现图片上传
date: 2023-02-03 14:22:25
tags: [Typora, PicGO, Github]
index_img: /img/typora.png
banner_img: /img/cat.JPG
---

## 参考
`文件--偏好设置--图像–上传服务` 2种方式安装参考博客

- [PicGo-Core (command line)](https://www.cnblogs.com/chonglu/p/16894257.html) ：Typora中直接 `下载或更新` 太慢

- [Custom Command](https://www.cnblogs.com/skuld-yi/p/14533794.html)：`npm` 本地安装 PicGo-Core以命令行方式配置图床

[typora-plugins-win-img](https://github.com/Thobian/typora-plugins-win-img)

## 安装 配置

![](https://github.com/Kukukukiki192/TyporaImg/blob/main/img/image-20230203120809911.png?raw=true)

`picgo use uploader` 后的图床配置 `~\.picgo\config.json`

```json
{
  "picBed": {
    "uploader": "github",  //当前默认上传图床
    "current": "github",
    "github": {
      "repo": "Kukukukiki192/TyporaImg",  //自己的仓库名
      "branch": "main",  //默认分支
      "token": "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",  // github的token
      "path": "img/",  //自定义存储路径(仓库下新建文件夹，可为空)
      "customUrl": "https://github.com/Kukukukiki192/TyporaImg/raw/main"  //自定义域名
      //https://github.com/[username]/[repo]/raw/[branch] 必须是该格式,不然用其它域名访问图片404本地加载失败
    },
    "transformer": "path"
  },
  "picgoPlugins": {}  // 为插件预留
}
```

## 图片上传服务设置和验证

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230203144056522.png)

按照参考建议：插入图片时先保存到本地以实现流畅的即时预览，在完成文章后统一批量上传 `格式–图像–上传所有本地图片(Format-Image-Upload All Local Images)`

## 上传图片失败问题

### 401 Unauthorized（未授权）

含义：服务器收到请求，但是你没有通过身份验证

常见原因：

① Token 错误或失效（最常见）
- GitHub Token 被删除
- Token 过期
- Token 权限不足
- 复制 Token 时多了空格
- 配置文件里还是旧 Token

检查 PicGo 配置，确认：
- token 是否最新
- 是否包含完整字符串
- 有没有引号问题

解决：更新 token

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230207151331420.png)

<div><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230207155156678.png" width=40% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230207155450598.png" width=60% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230207154220620.png" width=50% /><img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230207154627237.png" width=50% /></div>

② GitHub Token 权限不足

如果是 GitHub 图床，旧 token `repo` 权限需要 `Fine-grained token：Contents → Read and Write` 或 classic token 勾选 `repo`，否则上传时 GitHub API 会返回 `401 Bad credentials`

③ PicGo 没读取到你修改后的配置

Mac 常见. 若修改了 `~/.picgo/config.json` 但 Typora 调用的是另一个 PicGo，检查配置文件看 token 是否已更新
也可以测试上传图片，若失败，说明不是 Typora

### 422 Unprocessable Entity（请求格式错误）
含义：身份验证通过了，但是服务器无法处理你的请求

常见原因：

① GitHub 仓库路径配置错误

如 PicGo：
```
owner:kk1024
repo:image
path:img
```
实际 `https://github.com/kk1024/image` 不存在或仓库名大小写错误，如 `Images` 和 `images` 可能被 API 区分

② 文件名包含特殊字符

如 `截图 2026-07-24 下午3.20.png` 可能导致：`422 Validation Failed`，建议 PicGo 设置：`时间戳重命名` 或 `YYYYMMDD_HHMMSS`（`20260724_152030.png`）

③ GitHub 文件已经存在

GitHub API 创建文件：
```
PUT /repos/{owner}/{repo}/contents/{path}
```
若同名文件已存在，可能返回 `422`

解决： 重命名上传或开启时间戳 删除之前上传的同名文件

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230915213555559.png)

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230915214145277.png)

④ 图床接口限制

如 SM.MS：图片太大 / 频率限制