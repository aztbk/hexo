---
layout: post

title: "群晖：修改硬盘温度过高导致的关机"

categories: [技术分享]

tags: [群辉]

cover: https://img.5205230.xyz/file/AgACAgQAAyEGAASYGPkcAAMZaHL-ydkFmcsCWCJCSSzw3Ft9A7IAAvjJMRtUkphTpiCryMDNGqMBAAMCAAN3AAM2BA.png
 
date: 2024-08-18 10:00:00 +0800
---

# 群晖：修改硬盘温度过高导致的关机

## 备份文件

```
cp /usr/syno/etc.defaults/scemd.xml /usr/syno/etc.defaults/scemd.xml-20240818
```

## 打开文件修改

```
vi /usr/syno/etc.defaults/scemd.xml
```


### 将61替换为85

![图片](https://img.5205230.xyz/file/4dd26ded52c354cca85b1.jpg)


### 保存并退出

按键盘左上角的`exc`

`:wq`

### 重启设备

`reboot`
