# Typora + PicGO-Core(cmd安装方式) + Github 实现图片上传

## 参考
`文件--偏好设置--图像–上传服务` 2种方式安装参考博客

- [PicGo-Core (command line)](https://www.cnblogs.com/chonglu/p/16894257.html) ：Typora中直接 `下载或更新` 太慢

- [Custom Command](https://www.cnblogs.com/skuld-yi/p/14533794.html)：`npm` 本地安装 PicGo-Core以命令行方式配置图床

## 安装过程

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
|<img src="https://github.com/Kukukukiki192/TyporaImg/raw/main/img/image-20230203140441942.png" width=60% />|<img src="https://github.com/Kukukukiki192/TyporaImg/blob/main/img/image-20230203121421204.png?raw=true" width=40% />|
| --- | ---|
按照参考建议：插入图片时先保存到本地以实现流畅的即时预览，在完成文章后统一批量上传 `格式–图像–上传所有本地图片(Format-Image-Upload All Local Images)`











