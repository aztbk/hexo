---
layout: post

title: "永久免费vps serv00恢复到刚申请的状态"

categories: [白嫖分享]

tags: [serv00]

cover: https://img.5205230.xyz/file/AgACAgQAAyEGAASYGPkcAAMXaHL7dOisDWqutbAGnOad37tWkwwAAvXJMRtUkphTESGbK63bQwQBAAMCAAN5AAM2BA.jpg
 
date: 2024-09-02 10:00:00 +0800

---

# 永久免费vps serv00恢复到刚申请的状态

## 一、清除指定账户的所有进程

```
pkill -kill -u ${username}
```
`比如：pkill -kill -u admin`

## 二、删除文件夹及文件夹


### 1.更改非隐藏目录的权限

```
chmod -R 755 ~/*
```

### 2.更改隐藏目录的权限

```
chmod -R 755 ~/.*
```

## 三、删除文件夹及文件

### 1.删除非隐藏文件夹及其文件
```
rm -rf ~/*
```
### 2.删除非隐藏文件夹及其文件
```
rm -rf ~/.*
```

## 四、添加相应的文件

![文件树状图](https://img.5205230.xyz/file/195736ef039bc73e9d0c0.jpg)

### 1.添加`mail`文件
### 2.添加`repo`文件
### 3.添加`domains`文件
#### 添加一个文件，文件名为：`你的用户+.serv00.net`
#### 添加`logs`文件
#### 添加`pubic_html`文件
#### 最后添加`index.php`

**内容为：**

```
<!DOCTYPE html>
<html lang="pl">
    <head>
        <meta charset=utf-8 />
        <title>Sign in</title>
        <meta name="viewport" content="width=device-width, initial-scale=1.0">

        <link href="/static/bootstrap3/css/bootstrap.min.css" rel="stylesheet" media="screen" />

        <link href="/static/sass/devilweb.css?2.0.17.1" rel="stylesheet" media="screen" />
        <link href="/static/bootstrap-select/bootstrap-select.min.css" rel="stylesheet" media="screen" />
        <link href="/static/font-awesome/css/font-awesome.min.css" rel="stylesheet" media="screen" />

        <script type="text/javascript" src="/static/jquery/jquery.js"></script>
        <script type="text/javascript" src="/static/bootstrap3/js/bootstrap.min.js"></script>
        <script type="text/javascript" src="/static/bootstrap-select/bootstrap-select.min.js"></script>
        <script type="text/javascript" src="/static/common.js?2.0.17.1"></script>
        <script type="text/javascript">
            loaderForm('Please wait...');
        </script>
    </head>

    <body id="login_body" class="login_body_dark">
        <div class="background-container"></div>
        
    <div class="modal fade" id="language_modal" role="dialog" aria-hidden="true">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="modal-header">
                    <button type="button" class="close" data-dismiss="modal" aria-hidden="true">&times;</button>
                    <h4>Change language</h4>
                </div>
                <form class="form-horizontal" method="post" action="/lang/">
                <div class="modal-body">
                        <input type="hidden" name="csrfmiddlewaretoken" value="t23AOwubbak4L2pwyW1cKqoU4Nvq1e4Pw3JwCfNBVM09Hr3I7v3QCd0IXWfY0Qv4">
                        <div class="form-group">
                            <label class="col-md-3 control-label" for="inputEmail">Select language</label>
                            <div class="col-md-4">
                                <select name="language" id="id_language">
                                    
                                        <option value="pl">Polski</option>
                                    
                                        <option value="en">English</option>
                                    
                                </select>
                            </div>
                        </div>
                </div>
                <div class="modal-footer">
                    <button class="btn btn-default" data-dismiss="modal" aria-hidden="true"><i class="fa fa-times"></i> Close</button>
                    <button type="submit" class="btn btn-danger"><i class="fa fa-save"></i> Save changes</button>
                </div>
                    
                        <input type="hidden" name="next" value="/file_manager/index.php?secure_token=Kqo6OlHa4aoZYebYFHCwWS2g4MwezJdw&amp;get_action=get_content&amp;file=%2Fdomains%2Fyasmeen.serv00.net%2Fpublic_html%2Findex.html" />
                    
                </form>
            </div>
        </div>
    </div>

    <div class="centerlogin-wrapper">
    <div class="row login-fade" id="centerlogin" style="margin-top: -153px;">
        <div class="span4 offset4 well">
            <div class="login-content">
                <h3>Web interface SERV00.COM</h3>

                <form action="/login/" method="post">
                    <input type="hidden" name="csrfmiddlewaretoken" value="t23AOwubbak4L2pwyW1cKqoU4Nvq1e4Pw3JwCfNBVM09Hr3I7v3QCd0IXWfY0Qv4">
                    <div class="form-group"><label class="control-label" for="id_username">Username</label><input type="text" name="username" placeholder="Username" class="form-control span4" maxlength="60" title="" required id="id_username"></div>
<div class="form-group"><label class="control-label" for="id_password">Password</label><input type="password" name="password" placeholder="Password" class="form-control span4" title="" required id="id_password"></div>
                    
                        <input type="hidden" name="next" value="/file_manager/index.php?secure_token=Kqo6OlHa4aoZYebYFHCwWS2g4MwezJdw&amp;get_action=get_content&amp;file=%2Fdomains%2Fyasmeen.serv00.net%2Fpublic_html%2Findex.html" />
                    
                    <button id="submit" type="submit" name="submit" class="btn btn-info btn-block">Sign in</button>
                </form>
            </div>

            <div class="login-footer">
                <h5>No account yet?</h5>
                <p><a href="https://www.serv00.com/offer">Register</a> to use our management system.</p>

                
                    
                    <h5>Forgot your password?</h5>
                    <p><a href="/resetpass">Click here</a> to reset your password.</p>
                
            </div>
        </div>
        <div class="text-center post-login-box">
            &copy; 2008 - 2024 ADMIN.NET.PL &nbsp; &bull; &nbsp; All rights reserved<br>
            <a href="javascript:void(0);" onClick="$('#language_modal').modal(); return false;">Change language</a>
        </div>
    </div>
    </div>

    <script type="text/javascript">
        var $inputUsername = $("#id_username");
        var $passwordInput = $("#id_password");
        $inputUsername.focus();

        var $loginIcon = $('<span class="glyphicon glyphicon-user form-control-feedback text-muted" aria-hidden="true"></span>');
        $loginIcon.insertAfter($inputUsername);
        $inputUsername.parents('.form-group').addClass('has-feedback');

        var $passwordIcon = $('<span class="glyphicon glyphicon-lock form-control-feedback text-muted" aria-hidden="true"></span>');
        $passwordIcon.insertAfter($passwordInput);
        $passwordInput.parents('.form-group').addClass('has-feedback');
    </script>

    </body>

    <script type="text/javascript">
        var bigScreenWidth = 2500;
        var path = '/static/img/bg_normal.jpg';
        if (window.screen.width > bigScreenWidth) {
            path = '/static/img/bg_big.jpg';
        }
        var img = new Image();
        img.onload = function() {
            $('.background-container').addClass('loaded');
            if (window.screen.width > bigScreenWidth) {
                $('.background-container').addClass('big');
            }
        };
        img.src = path;

        $(document).ready(function () {
            setTimeout(function () {
                $("#centerlogin").removeClass('login-fade');
            }, 300);
            $('select').selectpicker();
        });
    </script>

</html>

```