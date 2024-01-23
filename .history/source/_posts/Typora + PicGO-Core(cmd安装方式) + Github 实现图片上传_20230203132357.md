# Typora + PicGO-Core(cmd安装方式) + Github 实现图片上传

`文件--偏好设置--图像–上传服务` 2种方式安装参考博客

- [PicGo-Core (command line)](https://www.cnblogs.com/chonglu/p/16894257.html) ：Typora中直接 `下载或更新` 太慢

- [Custom Command](https://www.cnblogs.com/skuld-yi/p/14533794.html)：`npm` 本地安装 PicGo-Core以命令行方式配置图床

安装过程

![image-20230203120809911](https://img.com/img/image-20230203120809911.png)

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
      "customUrl": "https://img.com"  //自定义域名
    },
    "transformer": "path"
  },
  "picgoPlugins": {}  // 为插件预留
}
```

图片上传服务设置和验证

 <img src="https://img.com/img/image-20230203121414930.png" alt="image-20230203121414930" style="zoom:50%;" /><img src="https://img.com/img/image-20230203121421204.png" alt="image-20230203121421204" style="zoom:50%;" />

按照参考建议

插入图片时先保存到本地以实现流畅的即时预览，在完成文章后统一批量上传 `格式–图像–上传所有本地图片(Format-Image-Upload All Local Images)`

由于Github原因，有时可能上传不成功，如果在编辑文档时上传，能显示Github地址，也表示上传成功，Typora不加载也没关系

 <img src="https://img.com/img/image-20230203123845205.png" alt="image-20230203123845205" style="zoom:67%;" />

 <img src="https://img.com/img/image-20230203123848182.png" alt="image-20230203123848182" style="zoom: 50%;" />

但是上传成功本地不加载，点击跳转图片src显示404，怀疑设置customUrl时和其他官方域名重复了，改下配置

 ![image-20230203131551342](https://Kukukukiki192_img.com/img/image-20230203131551342.png)





















