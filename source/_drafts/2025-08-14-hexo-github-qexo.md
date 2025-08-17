---
abbrlink: ''
categories:
- - 白嫖教程
cover: https://picgo91.cdn456.eu.org/20250814123521687.png
date: '2025-08-17'
layout: post
message: 欢迎来到我的博客，请输入密码以阅读。
password: Mignon999
tags:
- 'Qexo '
- Hexo
- 安知鱼
title: 利用Qexo 一个美观强大的在线静态博客管理器Hexo安知鱼主题+github
top_img: https://picgo91.cdn456.eu.org/20250814123521687.png
updated: '2025-08-17T10:49:19.941+08:00'
wrong_pass_message: 密码错误请重新输入!!
---
# 前言

**Hexo** 是一款快速、高效的静态博客框架。通过 **Markdown** 语法，只需几秒便可生成高质量的静态网页。

最近，我成功实现了在多设备间灵活管理博客并发布内容。一位网友提到 **Qexo**，一个为 **Hexo** 增加后台功能的工具，它让发布博客变得像发微博一样简单。深入了解后，我发现它非常强大，不仅可以用手机随时随地发表文章，还极大提升了操作便捷性。

尽管安装过程中遇到了一些问题，但最终都顺利解决。我将整理经验分享，希望能帮助更多人。

---

# Qexo 简介

**Qexo** 是一个快速、美观且功能丰富的在线**Hexo**管理器，支持通过 **Vercel** 免费部署，仅需配置一个数据库即可使用。

## 主要功能

* 自定义图床上传图片
* 在线编辑与页面管理
* 开放 API 接口
* 自动检查更新并一键更新
* 快速管理友情链接
* 短文分享（类似微博功能）
* 自动填充文章模板

**项目地址**：[Qexo 官方文档](https://www.oplog.cn/qexo/start.html)

---

## 一、Hexo博客搭建

> Hexo是个快速、简洁且高效的博客框架，它是一款基于Node.js的静态博客生成程序，作者是中国台湾tommy351。它的安装运行等甚至生成文章页面 生成目录，网站配置都是在爱代码模式下进行的。还有就是要学会使用Hexo，就得学会使用Git，并且对Git常用基础命令要有所了解，还有就是需要安装Node.js，这个软件是Hexo本地搭建必不可少的工具，值得一提的是Hexo博客可以部署到GitHub、Gitee、GitLab、Coding、七牛，都是完全免费的，可以让你实现免服务器，免域名搭建一个完整的博客。

### 1、安装git

Git是目前世界上最先进的分布式版本控制系统，可以有效、高速的处理从很小到非常大的项目版本管理。也就是用来管理你的hexo博客文章，上传到GitHub的工具。

**Windows：**下载并安装 git：[https://git-scm.com/download/win](https://isedu.top/index.php/goto?url=aHR0cHM6Ly9naXQtc2NtLmNvbS9kb3dubG9hZC93aW4=&cid=144)
对于中国大陆地区用户，可以前往 [淘宝 Git for Windows 镜像](https://isedu.top/index.php/goto?url=aHR0cHM6Ly9ucG0udGFvYmFvLm9yZy9taXJyb3JzL2dpdC1mb3Itd2luZG93cy8=&cid=144) 下载 git 安装包。

Linux (Ubuntu, Debian)：

```
sudo apt-get install git-core
```

Linux (Fedora, Red Hat, CentOS)：

```
sudo yum install git-core
```

### 2、安装nodejs

Hexo是基于**nodeJS**编写的，所以需要安装一下nodeJs和里面的npm工具。

windows：打开nodejs：[https://nodejs.org/en/download/](https://isedu.top/index.php/goto?url=aHR0cHM6Ly9ub2RlanMub3JnL2VuL2Rvd25sb2FkLw==&cid=144) 选择LTS版本。

linux：安装完后，打开命令行

```powershell
sudo apt-get install nodejs
sudo apt-get install npm
```

然后检查一下有没有安装成功

```powershell
node -v
npm -v
```

### 3、安装Hexo

先创建一个文件夹blog，在这个文件夹下的空白地方，右键git bash打开【Windows】，【Linux】如下

```powershell
mkdir blog
cd blog
```

然后安装hexo

```powershell
npm install -g hexo-cli
```

然后初始化hexo，这个`blog-demo`可以随便填

```powershell
hexo init blog-demo
```

用cd进入hexoblig里（或者直接打开这个文件夹，在空白地方右键 \**git bash打开\** ）

```powershell
cd blog-demo
```

这个时候`blog-demo`夹里有指定文件夹目录下有：

```powershell
node_modules: 依赖包
public：存放生成的页面
scaffolds：生成文章的一些模板
source：用来存放你的文章
themes：主题
_config.yml: 博客的配置文件
db.json：source解析所得到的
package.json：项目所需模块项目的配置信息
```

然后本地运行测试一下

```powershell
hexo clean && hexo g && hexo s
```

![img](https://picgo91.cdn456.eu.org/20250814105427706.png "img")

在浏览器输入 localhost:4000 就可以看到你生成的博客了。

**使用ctrl+c可以把服务关掉**

### 4.在GitHub创建一个放博客文件的仓库

没有账号的注册一个，登录后，点击右上角**New repository**

![img](https://picgo91.cdn456.eu.org/20250814111210051.png "img")

创建一个和你用户名相同的仓库，后面加.github.io，只有这样，将来要部署到GitHub page的时候，才会被识别，也就是xxx.github.io，其中xxx就是你注册GitHub的用户名。我这里是已经建过了。

点击**create repository**。

![img](https://picgo91.cdn456.eu.org/20250814111742821.png "img")

### 5. 生成SSH添加到GitHub

在博客hexoblog根目录 **右键点击 Git Bash Here**

```powershell
git config --global user.name "yourname"
git config --global user.email "youremail"
ssh-keygen -t rsa -C "youremail"
```

找到这个文件夹。打开 **id\_rsa.pub**

其中，**id\_rsa**是你这台电脑的私人秘钥，不能给别人看的，id\_rsa.pub是公共秘钥，可以随便给别人看。把这个公钥放在GitHub上，这样当你链接GitHub自己的账户时，它就会根据公钥匹配你的私钥，当能够相互匹配时，才能够顺利的通过git上传你的文件到GitHub上。

点击GitHub的右上角setting中 -> 点击左边SSH and GPG keys -> 点击New SSH key
title随便填，把C盘的**id\_rsa.pub**里面的信息复制到key里。

![img](https://picgo91.cdn456.eu.org/20250814113650285.png "img")

**查看是否成功**

```powershell
ssh -T git@github.com
```

这个时候要输入一次yes，如果前面生成ssh时设置了密码，需要输入密码，然后再回车

### 6. 将hexo部署到GitHub

打开站点配置文件_config.yml，拉到最后，修改为xxx就是你的GitHub账户

```powershell
deploy:
  type: git
  repo: git@github.com:xxx/xxx.github.io.git
  branch: main
```

> 注意：现在GitHub的默认分支已经是main了，不是master ！！！！

这个时候需要先安装**deploy-git**，也就是部署的命令,这样你才能用命令部署到GitHub

```powershell
npm install hexo-deployer-git --save
```

然后其中`hexo clean`清除了你之前生成的东西，`hexo deploy` 部署文章，可以用`hexo d`缩写

```powershell
hexo clean
hexo g
hexo deploy
```

输入hexo deploy之后会出现一个小弹窗，要你输入GitHub的username和password。（用户名是邮箱）

## 二、Github Actions自动化部署 Hexo博客

> 简单说，就是把hexo博客编译前的源代码上传到github代码仓库，Action在代码发生变动的时候，自动通过安装一系列nodejs环境和相关依赖，编译生成html页面到github pages仓库。
>
> 再简单点说，就是把本地生成博客的工作，全部交给Action执行。
>
> 好处就是随时随地都能修改或增加博文

### 1、先建一个私有仓库（自动化仓库）

先建一个私有仓库（hexo），这个仓库存放的是编译前的文件，也就是你电脑本地的文件，这个仓库是拿来做自动化的

![img](https://picgo91.cdn456.eu.org/20250814114243004.png "img")

**也就是一共两个仓库**

* 一个公有仓库存编译好的hexo（pages仓库，用户名例如是`xxx.github.io`）
* 一个私有仓库存**本地电脑编译前**的文件（自动化仓库，用户名是`hexo`）

### 2、上传编译前的代码

创建完私有仓库后，在本地博客文件中复制几个文件到另外一个文件夹，其中包括`.github`，`scaffolds`，`source`，`themes`，`_config.yml`，`package.json`，`package-lock.json`，`_config.anzhiyu.yml`

![img](https://picgo91.cdn456.eu.org/20250814114942160.png "img")

还有一个很重要的一步：打开themes/anzhiyu主题模板文件，`.git`文件删除，Hexo博客根目录修改配置文件使用anzhiyu主题

![img](https://picgo91.cdn456.eu.org/20250814115324009.png "img")

#### 1、上传`blog-demo`到`xxx.gitpub.io`这个仓库

然后回到`blog-demo`根目录右键打开git bash，上传到`xxx.gitpub.io`这个仓库

![img](https://picgo91.cdn456.eu.org/20250814120150691.png "img")

同样`SSH`和`HTTPS`均可。`SSH`在绑定过`ssh key`的设备上无需再输入密码，`HTTPS`则需要输入密码，但是`SSH`偶尔会遇到端口占用的情况。

#### 2、上传拷贝出来的文件到`hexo`仓库

方法和1的步骤相同，比如你拷贝出来的文件放hexo你就到文件夹hexo右击。

### 3、获取 Github token

打开[https://github.com/settings/tokens](https://isedu.top/index.php/goto?url=aHR0cHM6Ly9naXRodWIuY29tL3NldHRpbmdzL3Rva2Vucw==&cid=144)
点击 Generate new token 新建个 token

![img](https://picgo91.cdn456.eu.org/20250814120344425.png "img")

note随便填，Expiration选择No expiration，勾选repo和workflow，其他没什么了，然后点生成就好了

![img](https://picgo91.cdn456.eu.org/20250814120539361.png "img")

把token复制下来

![img](https://picgo91.cdn456.eu.org/20250814120735091.png "img")

打开自动化仓库hexo的`Settings<span> </span>`-> `Secrets and variables` -> `Actions` -> `New repository secret`

![](https://picgo91.cdn456.eu.org/20250814121043912.png)

一共有三个变量名`GITHUBTOKEN`，`GITHUBUSERNAME`，`GITHUBEMAIL`，逐一添加

![](https://picgo91.cdn456.eu.org/20250814121205008.png)


| 变量名         | 常量释义            |
| -------------- | ------------------- |
| GITHUBMAIL     | Github 用户邮箱地址 |
| GITHUBTOKEN    | Github token        |
| GITHUBUSERNAME | Github 用户名       |

### 4、添加workflows

接下来点击`Actions<span> </span>`-> `set up a workflow yourself`

![](https://picgo91.cdn456.eu.org/20250814121327464.png)

**复制以下代码到里面**

```
name: 自动部署

on:
  push:
    branches:
      - main

  release:
    types:
      - published

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: 检查分支
        uses: actions/checkout@v2
        with:
          ref: main

      - name: 安装 Node
        uses: actions/setup-node@v1
        with:
          node-version: "16.x"

      - name: 安装 Hexo
        run: |
          export TZ='Asia/Shanghai'
          npm install hexo-cli -g

      - name: 缓存 Hexo
        uses: actions/cache@v4
        id: cache
        with:
          path: node_modules
          key: ${{ runner.OS }}-${{ hashFiles('**/package-lock.json') }}

      - name: 安装依赖
        if: steps.cache.outputs.cache-hit != 'true'
        run: npm install --save

      - name: 生成静态文件
        run: |
          hexo clean
          hexo generate
          # 禁用 Jekyll
          echo "" > public/.nojekyll

      - name: 部署
        run: |
          cd ./public
          git init
          git config --global user.name '${{ secrets.GITHUBUSERNAME }}'
          git config --global user.email '${{ secrets.GITHUBEMAIL }}'
          git add .
          git commit -m "${{ github.event.head_commit.message }} $(date +"%Z %Y-%m-%d %A %H:%M:%S") Updated By Github Actions"
          git push --force --quiet "https://${{ secrets.GITHUBUSERNAME }}:${{ secrets.GITHUBTOKEN }}@github.com/${{ secrets.GITHUBUSERNAME }}/${{ secrets.GITHUBUSERNAME }}.github.io.git" master:main
```

**粘贴上去后点击Commit changes...**

![](https://picgo91.cdn456.eu.org/20250814121536652.png)

**就大功告成了，可以点击Actions查看运行进程了**

![](https://picgo91.cdn456.eu.org/20250814121632795.png)

# 三、通过 Vercel 部署 Qexo

## 1. 一键部署

点击以下按钮完成一键部署：[Vercel 一键部署](https://vercel.com/new/clone?repository-url=https://github.com/am-abudu/Qexo)

> **注意**：首次部署可能会出现错误提示，可忽略并继续后续步骤。

## 2. 修改 Node.js 版本

由于 **[Vercel 的已知问题](https://vercel.com/docs/functions/runtimes/python#python-dependencies)，需将项目的 Node.js 版本调整为** **18.x**。
路径：**Settings -> General -> Node.js Version**

## 3. 创建 Vercel 数据库

1. 进入[Vercel Storage 页面](https://vercel.com/dashboard/stores)。
2. 点击 **Create Database**，选择 **Neon** ，设置区域为 **Washington, DC., USA - iad1**，创建免费数据库。

## 4. 绑定项目

在 **Projects** 页面选择对应项目，点击 **Connect Project** 进行绑定。

## 5. 部署 Qexo

回到项目页面，点击**Redeploy** 开始部署。部署完成后，无报错即可访问域名进入初始化页面。

---

# 初始化配置

![](https://picgo91.cdn456.eu.org/20250814122313486.png)

![](https://picgo91.cdn456.eu.org/20250814122458597.png)

GitHub 配置

![](https://picgo91.cdn456.eu.org/20250814122606084.png)

填写博客源码所在仓库的分支名称，例如：

`main`

## GitHub 密钥

填写生成的 GitHub Token，例如：


| `wrq_P8sYPlYA9fjMlOPEYSKA84xxxxxxxxxxxxxx`<br/> |
| ----------------------------------------------- |

## 仓库路径

若 Hexo 源码在仓库根目录，则留空；否则填写路径：

![](https://picgo91.cdn456.eu.org/20250814123317560.png)

Vercel 配置

* **VERCEL\_TOKEN**：在[Vercel 账户设置](https://vercel.com/account/tokens) 中生成。
* **PROJECT\_ID**：在 **Project Settings -> General -> Project ID** 中找到。

配置完成后，即可登录后台管理博客内容。

![](https://picgo91.cdn456.eu.org/20250814123429876.png)

![](https://picgo91.cdn456.eu.org/20250814123521687.png)

![](https://picgo91.cdn456.eu.org/20250814123712814.png)
