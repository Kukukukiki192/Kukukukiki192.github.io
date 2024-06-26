---
title: macOS开发环境配置
date: 2024-02-03 19:53:10
tags: [MacOS, Homebrew, Git, Java, MySQL, Hexo, Typora, Python, VMware]
index_img: /img/macOS.png
banner_img: /img/dragon.jpg
---
# Homebrew

> 参考：[Mac包管理器Homebrew的安装方法](https://www.jb51.net/article/253389.htm)

## 自动脚本(全部国内地址)

```bash
# 安装
/bin/zsh -c "$(curl -fsSL https://gitee.com/cunkai/HomebrewCN/raw/master/Homebrew.sh)"
# 卸载
/bin/zsh -c "$(curl -fsSL https://gitee.com/cunkai/HomebrewCN/raw/master/HomebrewUninstall.sh)"
```

## 安装过程

![MacDE35](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE35.png)

`~/.zshrc`

```bash
# 配置homebrew环境变量
export HOMEBREW_HOME=/opt/homebrew
export PATH=$PATH:$HOMEBREW_HOME/bin
```

❗<font color=red>每次修改完配置文件都要通过 `source ～/.zshrc` 重新加载或者重启终端，使配置生效</font>

fix：后来 `echo $PATH` 检查输出包含了两次 `/opt/homebrew/bin`，重复写入了，删掉 `~/.zshrc` 中写入 `$PATH` 的路径. XXX_HOME不用删方便查看软件安装路径

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE1.png)

> 在 `$PATH` 中包含了 `/opt/homebrew/bin` 时，你已经拥有了 Homebrew 默认安装目录的权限，用 `which pkg_name` 命令检查若能够成功返回软件的可执行文件路径，则无需再手动添加软件的二进制文件路径到 `$PATH` 中，Homebrew 会为你管理这一切

## 默认 shell

若编辑的文件是`.bash_profile`，而关闭终端后发现每次重新打开终端都需要重新运行 `source ~/.bash_profile`，是因为 shell 配置文件没有在每次打开终端时自动加载

在 macOS 中，默认的终端应该在启动时自动加载 `.bash_profile`，但如果使用 Zsh 作为默认 shell，而环境变量配置写到了 `.bash_profile` 中，这可能导致 Zsh 无法读取到这些配置. Zsh 通常会读取 `~/.zshrc` 文件来加载配置

解决方法：

1. 把环境变量配置写到 `.zshrc` 中

2. 若想继续使用 `.bash_profile` 来管理环境变量，可在文件末尾添加一行来加载

    ```bash
    if [ -f ~/.zshrc ]; then
        source ~/.zshrc
    fi
    ```
    
3. 把默认 shell 换成 bash，重启终端生效

    ```bash
    echo $SHELL # 检查当前终端使用的默认 shell
    cat /etc/shells # 查看系统上安装的可用 shell
    chsh -s /path/to/new/shell # 更换默认 shell
    ```

    ![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE2.png)

    `The default interactive shell is now zsh.` 提示是 macOS 10.15 Catalina 版本以后默认切换到了 zsh 作为默认的 shell 后显示的.

    > Zsh（Z Shell）是Bash的一个强大的替代品，它提供了更好的命令补全、历史记录管理等功能. 它还支持用插件和脚本扩展其功能. 因此，将Zsh设置为默认Shell可以大大提高操作便利性和效率.

    zsh更好用，换回来  [什么是 zsh？我是否应该使用 zsh](https://www.poloxue.com/posts/2023-09-16-what-how-to-use-zsh/)

## 问题解决

![MacDE36](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE36.png)

`Error: Checksum mismatch.` 报错原因：Homebrew目录下的`portable-ruby-2.6.3_2.yosemite.bottle.tar.gz`文件引起的安装中断
解决方法：删掉对应路径文件，重新执行安装命令即可

---

![MacDE37](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE37.png)

安装 Core、Cask、services 时失败或卡住，按 `ctrl-c` 中断脚本执行 `git clone` 命令：

```bash
cd "$(brew --repo)/Library/Taps/"
mkdir homebrew && cd homebrew
git clone git://mirrors.ustc.edu.cn/homebrew-xxx.git
# eg.
k@KMac-mini ~ % cd /opt/homebrew/Library/Taps/homebrew
k@KMac-mini homebrew % ls
homebrew-cask		homebrew-core		homebrew-services
k@KMac-mini homebrew % sudo rm -rf homebrew-cask
Password:
k@KMac-mini homebrew % sudo git clone https://mirrors.ustc.edu.cn/homebrew-cask.git
Cloning into 'homebrew-cask'...
remote: Enumerating objects: 913406, done.
remote: Total 913406 (delta 0), reused 0 (delta 0), pack-reused 913406
Receiving objects: 100% (913406/913406), 440.35 MiB | 835.00 KiB/s, done.
Resolving deltas: 100% (664865/664865), done.
```

成功后继续执行安装命令(即重新运行安装脚本)，Homebrew会检测到已安装的部分并继续安装未完成的部分(我的不行还是重装了)

---

![MacDE38](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE38.png)

原因是 `Homebrew` 的根目录没有信任 `Homebrew/homebrew-core (no Git repository)` 和 `Homebrew/homebrew-cask (no Git repository)`，直接按照提示运行这两个命令行即可.
**装Homebrew时会自动安装Git**

## brew 命令

```bash
brew -v # 查看版本
brew update # 更新brew版本
brew upgrade 软件名 # 更新软件
brew search 软件名 # 搜索
brew install 软件名 # 安装
brew uninstall 软件名 # 卸载
brew ls # 本地软件库列表
brew list # 显示已安装软件
brew list 软件名 # 查看软件的安装目录及其内容
brew info 软件名 # 查看软件信息
brew home 软件名 # 用浏览器打开官方网页查看软件信息
brew outdated # 查看哪些已安装的程序需要更新
brew reps # 显示包依赖
brew help # 显示帮助
```
## 美化终端

[参考](https://www.poloxue.com/tags/zsh/)

1. 安装 [oh-my-zsh](https://www.itqaq.com/index/568.html) (流行的 zsh 框架)

    ```bash
    sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
    ```

    ![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE41.png)

2. 更换主题

    `~/.zshrc`

    ```bash
    # See https://github.com/ohmyzsh/ohmyzsh/wiki/Themes
    ZSH_THEME="passion" # 更换默认主题robbyrussell
    ```
- [内置主题](https://github.com/ohmyzsh/ohmyzsh/wiki/Themes)：看 `ZSH_THEME` 行上方链接
- [第三方主题](https://github.com/ohmyzsh/ohmyzsh/wiki/External-themes)：`clone` 到 `~/.oh-my-zsh/themes` 中使用
![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE42.png)

3. 配置插件

   `~/.zshrc`

   ```bash
   plugins=(git git-lfs z extract web-search zsh-autosuggestions zsh-syntax-highlighting you-should-use)
   ```
   
- [内置插件](https://github.com/ohmyzsh/ohmyzsh/wiki/Plugins)：[git](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/git)  [git-lfs](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/git-lfs) [z](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/z)  [extract](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/extract)  [web-search](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/web-search)

	`git` 插件：`alias | grep git` 查看别名，结合 `you-should-use` 插件使用更方便

- 第三方插件：`clone` 到 `~/.oh-my-zsh/custom/plugins` 中使用

    参考：[zsh、oh-my-zsh、提示主题与 7 效率插件](https://www.poloxue.com/posts/2023-10-16-zsh-themes-and-plugins/)  [6 个强大的 zsh 提效插件](https://www.poloxue.com/posts/2023-10-19-zsh-6-powerful-plugins/)  zsh资源合集：[awesome-zsh-plugins](https://github.com/unixorn/awesome-zsh-plugins)

    [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions/blob/master/INSTALL.md) 自动补全

    ```bash
    git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
    ```
    [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting/blob/master/INSTALL.md) 语法高亮

    ```bash
    git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
    ```

    [zsh-you-should-use](https://github.com/MichaelAquilina/zsh-you-should-use) 提示别名

    ```bash
    git clone https://github.com/MichaelAquilina/zsh-you-should-use.git $ZSH_CUSTOM/plugins/you-should-use
    ```

    [autojump](https://github.com/wting/autojump) `j DIR` 快速导航到常用目录

    `autojump` 根据访问频率和最近使用时间来智能推断目录  `z` 根据历史记录中的目录列表来匹配

    ```bash
    brew install autojump
    ```

    `source ~/.zshrc` 使生效，激活插件后效果：

    ![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE43.png)

我的 `~/.zshrc` 配置：

```bash
# Path to your oh-my-zsh installation.
export ZSH="$HOME/.oh-my-zsh"
# theme
ZSH_THEME="passion"
# plugins
plugins=(git git-lfs z extract web-search zsh-autosuggestions zsh-syntax-highlighting you-should-use)

source $ZSH/oh-my-zsh.sh
```

# Git

- **配置用户名和邮箱信息**

  ```bash
  git config --global user.name "username"
  git config --global user.email "email"
  ```

- **生成SSH Key**

  ```bash
  ssh-keygen -t rsa -C "本人GitHub绑定的邮箱" # 默认一路回车不要设置密码
  ```

- **在GitHub添加SSH Key**

  `Settings`--`SSH and GPG keys`--`new SSH key` 

  Title：自定义

  Key：填入`~/.ssh/id_rsa.pub`中生成的SSH Key字符串

  ![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE3.png)

- **验证配置**

  ```bash
  ssh -T git@github.com
  ```

  ![MacDE39](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE39.png)

# Java环境

## JDK

- 机型 系统版本

  ![MacDE40](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE40.png)

- Homebrew安装

  ```bash
  brew install openjdk
  ```

  (我用这个安装有点问题改成手动安装了)

- 手动安装

  [Java Download | Oracle](https://www.oracle.com/java/technologies/downloads)

  ![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE4.png)

  [bin.zip  bin.tar.gz  src.zip  src.tar.gz  rpm  dmg 区别](https://blog.csdn.net/danxiaodeshitou/article/details/134258750)

  ![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE5.png)

- 环境变量配置

  除了从 `关于本机` 查看芯片类型，还能用 `uname -a` 查看Mac是macOS x64(Intel)还是macOS ARM64(M)

  ```bash
  java -version # 验证安装
  /usr/libexec/java_home -V # 查看JDK安装路径
  # 配置JDK环境变量
  export JAVA21_HOME=/Library/Java/JavaVirtualMachines/jdk-21.jdk/Contents/Home
  export JAVA_HOME=$JAVA21_HOME
  export PATH=$PATH:$JAVA_HOME/bin
  export CLASSPATH=$JAVA_HOME/lib/tools.jar:$JAVA_HOME/lib/dt.jar:.
  alias jdk21='export JAVA_HOME=$JAVA21_HOME'
  # 验证配置
  java -version # 检查Java版本
  javac -version # 检查Java编译器版本
  ```

  ![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE6.png)

## Tomcat

- Homebrew安装

  ```bash
  brew install tomcat
  # 启动Tomcat
  catalina run # 或
  brew services start tomcat
  ```

- 手动安装

  [Tomcat下载和安装](https://c.biancheng.net/servlet2/tomcat-download.html) [Apache Tomcat](https://tomcat.apache.org/download-10.cgi)

  ![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE7.png)

- 环境变量配置

  (CSDN报错参考：“解压缩后，将文件放到library（即资源库）中，放到其他地方可能也行，但我放到其他地方在启动时会出错，因此参考了[Mac系统安装Tomcat终端出现-bash: startup.sh: command not found - 简书](https://www.jianshu.com/p/0938b1e538f5?utm_campaign=maleskine&utm_content=note&utm_medium=seo_notes)，将文件放在了library里”）

  ```bash
  export CATALINA_HOME=/Library/Tomcat/apache-tomcat-10.1.17
  export PATH=..:$CATALINA_HOME/bin
  ```

- 验证启动 http://localhost:8080

  ![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE8.png)

  ![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE9.png)

  `shutdown.sh` 关闭

## Maven

- 手动安装

  [Maven 环境配置](https://www.runoob.com/maven/maven-setup.html)

- Homebrew安装

  ```bash
  brew install maven
  mvn -v # 验证Maven安装
  brew list maven # 查找Maven安装路径
  ```

  ![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE10.png)

  ![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE11.png)

  ![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE12.png)

  添加环境变量：

  ```bash
  export MAVEN_HOME=/opt/homebrew/Cellar/maven/3.9.6
  ```

- 生成 `.m2` 文件夹

  ```bash
  mvn help:system
  ```

  ![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE13.png)

- 配置中央仓库镜像

  ```bash
  cd /opt/homebrew/Cellar/maven/3.9.6/libexec/conf # 安装目录
  vim settings.xml # 编辑配置文件
  <mirrors>
      <mirror>
          <id>aliyun</id>
          <mirrorOf>central</mirrorOf>
          <name>Aliyun Maven Central</name>
          <url>https://maven.aliyun.com/repository/central</url>
      </mirror>
  </mirrors>
  ```

  ![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE14.png)

- 配置本地仓库位置

  ![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE15.png)

  Maven 会使用默认路径 `~/.m2/repository`

  > `settings.xml` 补充说明（[原文](https://blog.csdn.net/pan_junbiao/article/details/104264644)）：
  > ![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE16.png)

- [IDEA配置Maven环境](https://c.biancheng.net/maven2/idea-maven-config.html)

  将本地安装的 Maven 配置到 IntelliJ IDEA 中，不用 IDEA 自带的 Maven

  ![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE17.png)

  免费的IDEA社区版创建不了SpringBoot项目 参考：[利用IDEA社区版创建SpringBoot项目的详细图文教程](https://www.jb51.net/article/281303.htm)

# MySQL

## 安装过程

```bash
brew search mysql
brew install mysql
brew services start mysql # 启动MySQL服务
mysql_secure_installation # 设置MySQL根密码 psw:11001100
```

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE18.png)

添加环境变量：

```bash
export MYSQL_HOME=/opt/homebrew/Cellar/mysql/8.2.0_1
```

## DataGrip连接MySQL

> DataGrip激活：公众号-安哥说后端 [激活工具](https://chenjunan.top/img/jetbra.zip) [datagrip激活码](https://chenjunan.top/img/activate/datagrip-new.txt) [图文激活教程](www.bilibili.com/read/cv28362142)

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE19.png)

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE20.png)

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE21.png)

# [Hexo配置](https://hexo.io/zh-cn/)

前提：Git ✅ [Node.js](https://www.runoob.com/nodejs/nodejs-tutorial.html)

```bash
brew install node # 安装node
node -v
npm -v
npm install hexo-cli -g # 安装hexo
npm install hexo # 熟悉npm的可仅局部安装hexo包
hexo -v
```

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE22.png)


> [NPM](https://www.runoob.com/nodejs/nodejs-npm.html)是随同NodeJS一起安装的包管理工具，能解决NodeJS代码部署上的很多问题，由于新版的nodejs已经集成了npm，所以之前npm也一并安装好了

```bash
npm install xx # 本地安装
npm install -g xx # 全局安装
npm uninstall xxx # 卸裁模抉
npm update xx # 更新模块
npm search xx # 搜索模块
```

- 发布前配置好1️⃣ ssh_key ✅ 2️⃣ `_config.yml` 中 deploy 部分

  ![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE23.png)

  ```bash
  cd ~/Document/kblog
  hexo init
  npm install # 根据package.json文件中的依赖项列表安装所有必要的包
  hexo g # 生成
  hexo s # 启动服务
  npm install hexo-deployer-git --save # 安装部署插件
  hexo d # 部署到github 
  ```

- [多台电脑操作hexo个人网站](https://blog.csdn.net/Zhangxiaorui_9/article/details/79723288?spm=1001.2101.3001.6650.1&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-79723288-blog-105105705.235%5Ev40%5Epc_relevant_anti_t3_base&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-79723288-blog-105105705.235%5Ev40%5Epc_relevant_anti_t3_base&utm_relevant_index=2)

  ![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE24.png)

  ![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE25.png)

  ![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE26.png)

  之后每次换电脑更新博客前先git pull

# Typora

## 激活

[Typora官网](https://typoraio.cn) 下载后在`/Applications/Typora.app/Contents/Resources/TypeMark/page-dist/static/js` 路径下找到LicenseIndex开头的js文件，把 `e.hasActivated="true"==e.hasActivated` 改为 `e.hasActivated="true"=="true"`

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE27.png)

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE28.png)

## 图床配置

[Typora + PicGO-Core(cmd安装方式) + Github 实现图片上传](https://kk1024.cool/2023/02/03/TyporaImg)

- 安装

  npm在本地安装PicGo-Core

  ![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE29.png)

- 配置

  交互式命令行配置并自动生成配置文件

  ![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE30.png)

- Typora设置

  ![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE31.png)

  ```bash
  npm install picgo -g #安装PicGo-Core
  picgo set uploader #交互式命令行配置
  picgo use uploader #选择当前要使用的Uploader
  #配置文件 ~/.picgo/config.json
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
  #上传的图片地址
  https://raw.githubusercontent.com/Kukukukiki192/TyporaImg/main/img/icon_512x512.png
  https://github.com/Kukukukiki192/TyporaImg/raw/main/img/icon_512x512.png
  ```

# Dash

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE32.png)

# Python

[Mac下的Pycharm教程](https://www.jianshu.com/p/dc396a37ddee)

anaconda = python + （NumPy、SciPy 等常用第三方库 ）+ IDE

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE33.png)

[学习 python 必须弄懂的 Python、Pycharm、Anaconda 三者之间的关系](https://zhuanlan.zhihu.com/p/142657444)

[anaconda和python的区别](https://m.py.cn/faq/python/15704.html)

安装新的python前要确保以前的卸载干净

# VMware Fusion

[VMware Fusion英文官网](https://my.vmware.com/web/vmware/evalcenter?p=fusion-player-personal)  针对个人用户免费 [macOS安装VMware操作记录](https://github.com/Kukukukiki192/Info/blob/master/vmQ%26A)

注册账号并申请序列号，必须用英文官网打开. 用goole chrome打开会自动跳转到中文网站，改用Safari才行. 按提示注册后，会出现序列号，复制出来，下载dmg文件安装时使用即可

> 注：VMware12版本需要macOS11.0以上，此macOS10.13不能使用，需要安装VMware11.5

[MacOS系统版本和VMware各版本适配情况](https://kb.vmware.com/s/article/2088571)

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/MacDE34.png)