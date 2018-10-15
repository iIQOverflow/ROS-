# ROS版本
Kinetic
# 烧录系统
烧录已经预装ROS系统的Ubuntu系统到SD卡。
- 下载Linux系统（ubuntu，预装kinetic），[下载地址](https://downloads.ubiquityrobotics.com/pi.html)。
- 安装[Etcher](https://etcher.io/)。
- 使用Etcher烧录linux系统至SD卡中。
- 系统的初始账号密码都为ubuntu。
# 系统配置
树莓派连接显示屏、键盘、网线、电源后开机。
## SSH连接
- 树莓派开机后登录系统，账号：ubuntu，密码：ubuntu。
- CTRL+ALT+T打开终端，输入ifconfig查看ip地址。
- PC端启动PuTTY输入ip，选择SSH，点击连接。
- 在SSH界面中输入账号密码，进入系统，SSH登录成功。
## VNC配置
- 通过SSH界面安装vncserver
```
sudo apt install xfce4 xfce4-goodies tightvncserver

```
- 配置vncserver文件
```
vim ~/.vnc/xstartup
```
- 替换所有内容
```
#!/bin/bash
xrdb $HOME/.Xresources
startxfce4 &
```
- 赋予可执行权限
```
sudo chmod +x ~/.vnc/xstartup
```
- 启动vncserver
```
启动vncserver
```
- 设置vncserver密码
- 下载后打开vnc viewer软件，输入 ip地址:端口号 后，点击连接，输入密码，连接成功。
[参考](https://blog.csdn.net/tuzixini/article/details/78994007)
