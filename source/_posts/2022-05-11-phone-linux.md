---

layout: post

title: "给旧手机装个linux后，还能装个啥？比如装一个宝塔面板？"

categories: [技术分享]

tags: [旧手机应用, 宝塔面板]

cover: https://img.5205230.xyz/file/899ed6e65ca7a49fb13db.png
 
date: 2022-05-10 12:00:00 +0800
 
---


> 上面讲的是如果安装一个linux系统到手机上，图形化使用。这就开始讲讲最简单的方式来配置linux服务器吧！


## 安装`AidLux`。

这个直接在应用商店下载就好了，打开后不用登录直接免登录使用，然后我们点击`cloud_ip`，打开它，会显示一个网址，在电脑上输入这个网址，就可以远程访问了，直接电脑操作，方便多了！

![图片](https://img.5205230.xyz/file/a2f22920e4ef9dfcafdb8.png)

![图片](https://img.5205230.xyz/file/50d5a4403c7fce1958064.png)

![图片](https://img.5205230.xyz/file/0e9d2de3442d58a282678.png)

![图片](https://img.5205230.xyz/file/899ed6e65ca7a49fb13db.png)

电脑打开后就是这样子了！

![图片](https://img.5205230.xyz/file/19651d5c77d5a289e15fc.png)

这个时候，我们就可以把他当作一个正常的服务器来使用了！

## 安装一个宝塔软件吧！

### 安装宝塔

```
apt update
```
```
apt upgrade
```
```
sudo curl -sSO https://download.bt.cn/install/install_panel.sh;sudo bash install_panel.sh
```
```
chmod a+x install_panel.sh
```
```
chmod -R 777 /www
```
```
./install_panel.sh
```
```
chmod 777 /www/server -R
```

以上的步骤就是按照宝塔的命令了。最后可能会说启动失败，没关系，接下来继续操作！

![图片](https://img.5205230.xyz/file/5873756b75d5b600c1484.png)

### 查看宝塔信息

输入以下命令：

```
sudo bt
```

就可以看到以下的界面，然后`选择1`就可以启动了。这里建议后面再`选择6和5`修改用户名以及密码。

![图片](https://img.5205230.xyz/file/221a83da4afa81344b03c.png)

最后`选择14`，查看宝塔面板的默认信息，也就是登录网址，账号密码啥的。

![图片](https://img.5205230.xyz/file/ed2cafc7b910a5e4bce7e.png)

然后在浏览器打开这个网址，输入用户名密码就可以啦！

![图片](https://img.5205230.xyz/file/c1505e1f7da3edde0b5f1.png)

有了宝塔面板就方便多了，很多东西都方便安装了！
