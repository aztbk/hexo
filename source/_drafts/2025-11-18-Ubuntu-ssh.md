---
abbrlink: ''
categories: []
cover: https://picgo91.cdn456.eu.org/20251118075449677.jpeg
date: '2025-11-18T07:22:25.947+08:00'
layout: post
message: ''
password: ''
tags: []
title: 在Ubuntu中启用root账号并开启ssh
top_img: https://picgo91.cdn456.eu.org/20251118075449677.jpeg
updated: '2025-11-18T07:22:25.947+08:00'
wrong_pass_message: ''
---
## 在Ubuntu上开启SSH服务可以通过以下步骤完成：

### 1. 安装SSH服务器

打开终端并执行：

```
sudo apt update
sudo apt install openssh-server
```

### 2. 启动SSH服务

安装后服务通常会自动启动。如需手动控制：

```
sudo systemctl start ssh
sudo systemctl enable ssh
```

### 3. 检查服务状态

```
sudo systemctl status ssh
```

正常状态会显示** **`active (running)`

### 4. 配置防火墙（如果启用）

允许SSH默认端口22：

```
sudo ufw allow ssh
# 或指定端口
sudo ufw allow 22/tcp
```

### 5. 连接测试

在另一台机器上使用以下命令连接：

```
ssh username@ubuntu_ip_address
```

### 可选配置（高级）

* **修改端口**：编辑** **`/etc/ssh/sshd_config`修改** **`Port`值
* **禁用密码登录**：在配置文件中设置** **`PasswordAuthentication no`（需先配置密钥登录）
* **重启服务生效**：`sudo systemctl restart ssh`

### 注意事项

* 通过** **`ip addr`查看本机IP地址
* 确保客户端和服务器在同一网络
* 公共网络建议使用密钥认证替代密码

完成以上步骤后，即可通过SSH远程访问Ubuntu系统。

## 在Ubuntu中启用root账号需要以下步骤：

### 1. 设置root密码

```
sudo passwd root
```

然后输入两次新密码。

### 2. 启用root登录（可选，根据需求选择）

#### 方法一：允许root通过密码SSH登录

编辑SSH配置文件：

```
sudo nano /etc/ssh/sshd_config
```

找到并修改以下行：

```
#PermitRootLogin prohibit-password
PermitRootLogin yes
```

或者如果显示：

```
#PermitRootLogin yes
```

直接取消注释（删除#号）

#### 方法二：允许root通过密钥登录（推荐）

```
PermitRootLogin without-password
```

### 3. 重启SSH服务

```
sudo systemctl restart ssh
```

### 4. 测试root登录

```
ssh root@服务器IP地址
```

### 安全建议

#### ⚠️ 重要安全考虑：

1. **不推荐直接启用root登录**- 更安全的方式是使用普通用户登录，然后`su`或`sudo -i`切换root
2. **如果必须启用**，建议：

   * 使用密钥认证替代密码
   * 限制登录IP
   * 修改默认SSH端口

#### 更安全的替代方案：

```
# 使用普通用户登录后切换root
ssh username@ip
sudo -i

# 或使用su
su -
```

#### 禁用root登录（如需恢复）：

编辑`/etc/ssh/sshd_config`：

```
PermitRootLogin no
```

请根据实际安全需求谨慎选择是否启用root远程登录。
