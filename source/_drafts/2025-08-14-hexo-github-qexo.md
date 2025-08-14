---
abbrlink: ''
categories:
- - 白嫖教程
cover: https://13fe9ff.webp.li/2024/11/6a16b8185a435cf9b807dbcc894d92e1.png
date: '2025-08-14T08:20:54.576+08:00'
layout: Post
tags:
- Qexo
- Hexo
- github
title: Qexo 一个美观,强大的在线,静态博客管理器Hexo+github+qexo
top_img: https://img.090227.xyz/file/ae62475a131f3734a201c.png
updated: '2025-08-14T08:20:54.576+08:00'
---
# 前言

**Hexo** 是一款快速、高效的静态博客框架。通过 [Markdown](http://daringfireball.net/projects/markdown/) 语法，只需几秒便可生成高质量的静态网页。

最近，我成功实现了在多设备间灵活管理博客并发布内容。一位网友提到 **Qexo**，一个为 Hexo 增加后台功能的工具，它让发布博客变得像发微博一样简单。深入了解后，我发现它非常强大，不仅可以用手机随时随地发表文章，还极大提升了操作便捷性。

尽管安装过程中遇到了一些问题，但最终都顺利解决。我将整理经验分享，希望能帮助更多人。

---

# Qexo 简介

**Qexo** 是一个快速、美观且功能丰富的在线 Hexo 管理器，支持通过 Vercel 免费部署，仅需配置一个数据库即可使用。

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

# 一、配置 GitHub 自动化部署

## 1. 获取 GitHub Token

1. 打开 **Personal settings** -> **Developer settings** -> **Personal access tokens**
2. 设置权限为 **repo** 和 **public repo**

[![图示1](https://13fe9ff.webp.li/2024/11/313f2ca0d7d3ea811d7e7be8ad6bcd4b.png)](https://13fe9ff.webp.li/2024/11/313f2ca0d7d3ea811d7e7be8ad6bcd4b.png)

3. 保存生成的 Token（丢失后无法恢复，只能重新生成）
4. 在博客代码仓库的 **Secrets** 中添加名为 **PERSONAL\_TOKEN** 的变量，后续步骤将用到。

[![](https://13fe9ff.webp.li/2024/11/f69e8dd9266ba1336ddddff00a67ffc6.png)](https://13fe9ff.webp.li/2024/11/f69e8dd9266ba1336ddddff00a67ffc6.png)

## 2. 创建 GitHub Actions

1. 在博客仓库页面，点击 **Actions**。
2. 选择 **Set up a workflow yourself**。

[![](https://13fe9ff.webp.li/2024/11/b425061c44375abea8ca5a8a01091038.png)](https://13fe9ff.webp.li/2024/11/b425061c44375abea8ca5a8a01091038.png)

3. 输入以下 YAML 配置并点击 **Start commit** ：

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

---

# 二、通过 Vercel 部署 Qexo


## 1. 一键部署

点击以下按钮完成一键部署：[Vercel 一键部署](https://vercel.com/new/clone?repository-url=https://github.com/am-abudu/Qexo)

> **注意**：首次部署可能会出现错误提示，可忽略并继续后续步骤。

## 2. 修改 Node.js 版本

由于 **[Vercel 的已知问题](https://vercel.com/docs/functions/runtimes/python#python-dependencies)，需将项目的 Node.js 版本调整为** **18.x**。
路径：**Settings -> General -> Node.js Version**

## 3. 创建 Vercel 数据库

1. 进入[Vercel Storage 页面](https://vercel.com/dashboard/stores)。
2. 点击 \***Create Database**，选择 **Neon** ，设置区域为 **Washington, DC., USA - iad1**，创建免费数据库。

## 4. 绑定项目

在 **Projects** 页面选择对应项目，点击 **Connect Project** 进行绑定。

## 5. 部署 Qexo

回到项目页面，点击**Redeploy** 开始部署。部署完成后，无报错即可访问域名进入初始化页面。

---

# 初始化配置

[![](https://13fe9ff.webp.li/2024/11/d14a6a28fa42dc905ad1f9572d280abb.png)](https://13fe9ff.webp.li/2024/11/d14a6a28fa42dc905ad1f9572d280abb.png)

[![](https://13fe9ff.webp.li/2024/11/8781b5e062a34509ccf39ed0000e8033.png)](https://13fe9ff.webp.li/2024/11/8781b5e062a34509ccf39ed0000e8033.png)

## GitHub 配置

[![](https://13fe9ff.webp.li/2024/11/7f4e9a472b66f4a2b73ae1c8e035b4ef.png)](https://13fe9ff.webp.li/2024/11/7f4e9a472b66f4a2b73ae1c8e035b4ef.png)
填写博客源码所在仓库的分支名称，例如：


| `master`<br/> |
| ------------- |

## GitHub 密钥

填写生成的 GitHub Token，例如：


| `wrq_P8sYPlYA9fjMlOPEYSKA84xxxxxxxxxxxxxx`<br/> |
| ----------------------------------------------- |

## 仓库路径

若 Hexo 源码在仓库根目录，则留空；否则填写路径：


| `path/`<br/> |
| ------------ |

[![](https://13fe9ff.webp.li/2024/11/f2f7c6b57196afa6652292807698db91.png)](https://13fe9ff.webp.li/2024/11/f2f7c6b57196afa6652292807698db91.png)

[![](https://13fe9ff.webp.li/2024/11/5e4c876cd000a6d5f5da45bb256c963e.png)](https://13fe9ff.webp.li/2024/11/5e4c876cd000a6d5f5da45bb256c963e.png)

[![](https://13fe9ff.webp.li/2024/11/bcc3ab289c7a355ed8116d92faddba80.png)](https://13fe9ff.webp.li/2024/11/bcc3ab289c7a355ed8116d92faddba80.png)

## Vercel 配置

* **VERCEL\_TOKEN**：在[Vercel 账户设置](https://vercel.com/account/tokens) 中生成。
* **PROJECT\_ID**：在 **Project Settings -> General -> Project ID** 中找到。

配置完成后，即可登录后台管理博客内容。

[![](https://13fe9ff.webp.li/2024/11/df6b8e762d048854683e5e31f6e262f2.png)](https://13fe9ff.webp.li/2024/11/df6b8e762d048854683e5e31f6e262f2.png)

[![](https://13fe9ff.webp.li/2024/11/2fa7cd4b16b469345b8e628d88affae2.png)](https://13fe9ff.webp.li/2024/11/2fa7cd4b16b469345b8e628d88affae2.png)

[![](https://13fe9ff.webp.li/2024/11/6a16b8185a435cf9b807dbcc894d92e1.png)](https://13fe9ff.webp.li/2024/11/6a16b8185a435cf9b807dbcc894d92e1.png)

---
