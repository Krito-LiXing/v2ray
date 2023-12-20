# 一键搭建Trojan-Go面板，配合使用CDN+Websocket，免费开启CDN隐藏自己VPS的真实IP，保护VPS永不被墙
## 准备工作
## 谷歌云Google Cloud Platform开启SSH访问及设置root访问密码

使用root用户登录，使用sudo -i切换登录身份

设置root密码，使用passwd命令设置root密码

修改SSH配置文件
```
vim /etc/ssh/sshd_config
```
找到以下内容并修改；
PermitRootLogin yes //默认为no，需要开启root用户访问改为yes
PasswordAuthentication yes //默认为no，改为yes开启密码登陆

修改完成之后重启

## 搭建Trojan-go面板

### 开启Debian10自带的BBR加速
## Installation 安装方法  

#### Usage 脚本使用方法
```bash
bash <(curl -Lso- https://git.io/kernel.sh)
```
#### 通过 curl 命令安装  via curl to install script

```bash
curl -O https://raw.githubusercontent.com/jinwyp/one_click_script/master/install_kernel.sh && chmod +x ./install_kernel.sh && ./install_kernel.sh
```

#### 通过 wget 命令安装 Linux 内核 和 Wireguard  via wget to install script

```bash
wget --no-check-certificate https://raw.githubusercontent.com/jinwyp/one_click_script/master/install_kernel.sh && chmod +x ./install_kernel.sh && ./install_kernel.sh
```

![功能列表3](https://github.com/jinwyp/one_click_script/blob/master/docs/readme3.png?raw=true)
    ## 使用说明 Usage 

### kernel
### 安装 linux 新版内核 开启BBR 或 BBR Plus 加速


1. CentOS / AlmaLinux / Rocky Linux 系统安装新版 linux 内核. 运行脚本后 请选择31 安装官方源最新版5.16内核 或选择35 安装 LTS 5.10 内核 推荐安装 LTS 5.10. 根据提示需要重启2次 完成内核安装。
2. Debian / Ubuntu 系统安装新版 linux 内核. 运行脚本后 Debian 请选择41 安装 LTS 5.10 内核, Ubuntu 请选择45 安装 LTS 5.10 内核. 根据提示需要重启2次 完成内核安装。
3. 开启 BBR 网络加速. 完成上面更换新内核后, 重新运行脚本后 选择2 然后根据提示选择 BBR 加速, 推荐使用BBR + Cake 组合算法.
4. 安装BBR Plus 内核并开启 BBR Plus. 运行脚本后 选择61 安装原版4.14.129版本 BBR Plus 内核, 或选择66 安装5.10 LTS BBR Plus内核. 安装完成重启2次后, 重新运行脚本后 选择3 根据提示开始 BBR Plus. 
5. 注意安装过程中 如果弹出大框的英文提示(下面有示例图) "安装linux内核有风险是否终止", 要选择" NO" 不终止. 安装完毕会重启VPS.

![注意 安装BBR plus](https://github.com/jinwyp/one_click_script/blob/master/docs/debian.jpg?raw=true)
![注意 安装BBR plus](https://github.com/jinwyp/one_click_script/blob/master/docs/kernel.png?raw=true)
![注意 安装BBR plus](https://github.com/jinwyp/one_click_script/blob/master/docs/ubuntu.png?raw=true)
## 更新系统安装环境

1、Debian/Ubuntu系统执行以下命令：。

    apt update -y && apt install -y curl
    
    
2、CentOS系统执行以下命令：

    yum update -y && yum install -y curl 
    
## Jrohy的一键Trojan面板脚本
### #安装/更新

    source <(curl -sL https://git.io/trojan-install)
    
### #卸载

    source <(curl -sL https://git.io/trojan-install) --remove
    
    
### 安装过程中，会出现3次提示，请根据以下选项进行：

- 1、第一次需要选择1. Let’s Encrypt证书
   请输入申请证书的域名：host.kjxlu.com
   
- 2、选择‘1. 安装docker版mysql’
   回车或手动输入用户名
   
注：跑完以上代码后，最后会出现一个选择菜单，不用理会，直接回车退出即可，即回到#提示符的状态下。至此，Trojan-Go面板搭建完成。

    
### 安装完后输入'trojan'可进入管理程序

浏览器访问 https://域名，可在线web页面管理trojan用户

第一次登陆面板时，会让您输入登陆密码，输入完后请使用用户名‘admin’及您设置的密码登陆。

-----------------------------------

## Trojan-Go 设置

### 登陆面板，修改Trojan类型为Trojan-Go

<div align=center><img src="https://github.com/KEJIXIAOLU/Trojan/blob/main/%E6%9C%AA%E6%A0%87%E9%A2%98-3.jpg"  /></div>

## 更改Trojan-Go配置文件
找到VPS目录文件 /usr/local/etc/trojan/config.json ，备份一份（若是把类型切换回来可以恢复使用Trojan）。

对着config.json文件按鼠标右键，选择‘用记事本编辑’。
## 更改配置参数：
### *注意：要在mysql的大括号}后加一个英文的逗号。路径和域名需要在客户端匹配。

         "websocket": {
        "enabled": true,
        "path": "/DFE4545DFDED/",
        "host": "你的域名"
       },
        "mux": {
        "enabled": true,
        "concurrency": 8,
        "idle_timeout": 60
        }



<div align=center><img src="https://github.com/KEJIXIAOLU/Trojan/blob/main/%E6%9C%AA%E6%A0%87%E9%A2%981.png"  /></div>

1、/DFE4545DFDED/为路径，随意填写。
2、host后 填上你的域名




