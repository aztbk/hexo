---
abbrlink: ydcdnk80
categories: []
cover: https://img.090227.xyz/file/ae62475a131f3734a201c.png
date: null
layout: post
message: 欢迎来到我的博客，请输入密码以阅读。
password: '@KY66812'
tags: []
title: 移动CDNK搭建命令
top_img: https://img.090227.xyz/file/ae62475a131f3734a201c.png
updated: '2025-10-02T16:55:30.699+08:00'
wrong_pass_message: 密码错误请重新输入
---
# 移动CDNK搭建命令

## 第一次运行：

```
cd /etc && wget https://picgo91.github.io/CDNK && chmod 744 /etc/CDNK && ./CDNK -q 80 -w 5 -c 3
```

## 停止CDNK.service：

```
sudo systemctl stop CDNK.service
```

## 停止开机启动CDNK.service：

```
sudo systemctl disable CDNK.service
```

## 检查CDNK.service是否关闭：

```
sudo systemctl status CDNK.service
```

## 停止程序：

```
pkill -f CDNK
```

## 删除服务文件：

```
sudo rm /etc/systemd/system/CDNK.service
```

## 检查是否已删除：

```
systemctl list-unit-files | grep CDNK.service
```

## 删除程序：

```
sudo rm /etc/CDNK
```

## 检查是否已删除

```
systemctl list-unit-files | grep CDNK
```
