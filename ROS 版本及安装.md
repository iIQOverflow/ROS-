# 版本问题
目前（2018年8月）ROS官方网站长期支持的有两个安装版本
- ROS Kinetic Kame （2016年5月发布，支持至2021年8月）
- ROS Melodic Morenia （2018年5月发布，支持至2023年8月）
这次我安装的是比较新的版本Melodic。不过两者差别不是特别大，Kinetic发布时间比较长，BUG修复的比较多，网上资料也会相对多一些，
Melodic可能新特性比较多，个人猜测。
# 安装ROS Melodic教程

1. 登陆[ROS官方网站](www.ros.org)，如图![image](https://github.com/iIQOverflow/ROS-Learning/blob/master/images/ROS%20Website.png)
2. 任选一款产品，点击Download，这里以Melodic为例。
3. 选择适合自己的平台，如Ubuntu，Debian，Arch Linux等，这里我选择的是Ubuntu。![image](https://github.com/iIQOverflow/ROS-Learning/blob/master/images/ROS%20Installation.png)
4. 设置source源
```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```
5. 设置keys
```
sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 421C365BD9FF1F717815A3895523BAEEB01FA116
```
6. 更新包目录
```
sudo apt-get update
```
7. 正式安装ROS，注意ROS Melodic有许多版本，如全桌面版，桌面版，基本版等，为了方便起见，这里安装Desktop-Full，也是官方推荐的。
```
sudo apt-get install ros-melodic-desktop-full
```
8. 初始化rosdep
```
sudo rosdep init
rosdep update
```
9. 环境设置
```
echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc
source ~/.bashrc
```
