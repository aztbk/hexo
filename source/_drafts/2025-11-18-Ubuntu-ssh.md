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
updated: '2025-11-18T08:45:01.162+08:00'
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


## 在Ubuntu图形界面（GUI）中启用root登录需要以下步骤：

### ⚠️ 安全警告

**强烈不推荐启用root图形登录**，因为这会带来严重安全风险。建议使用普通用户登录，然后在终端中使用`sudo`或`su`。

如果确实需要，请按以下步骤操作：

#### 1. 首先设置root密码（如果未设置）

```
sudo passwd root
```

#### 2. 启用root图形登录

##### 对于Ubuntu（使用GDM）：

```
sudo nano /etc/gdm3/custom.conf
```

找到并修改以下行：

```
# 禁用自动登录（如果有）
AutomaticLoginEnable=false

# 允许root登录（添加或修改）
AllowRoot=true
```

##### 对于使用LightDM的系统：

```
# 创建LightDM配置目录（如果不存在）
sudo mkdir -p /etc/lightdm/lightdm.conf.d

# 编辑配置文件
sudo nano /etc/lightdm/lightdm.conf.d/50-enable-root-login.conf
```

添加以下内容：

```
[Seat:*]
allow-guest=false
greeter-show-manual-login=true
greeter-hide-users=false
```

#### 3. 修改PAM认证配置

```
# 备份原配置
sudo cp /etc/pam.d/gdm-password /etc/pam.d/gdm-password.bak

# 编辑PAM配置
sudo nano /etc/pam.d/gdm-password
```

注释掉或删除以下行（通常在文件开头）：

```
auth    required        pam_succeed_if.so user != root quiet_success
```

#### 4. 重启显示管理器

```
# 重启GDM
sudo systemctl restart gdm3

# 或者重启LightDM
sudo systemctl restart lightdm
```
