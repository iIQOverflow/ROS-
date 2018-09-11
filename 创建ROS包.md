# ROS包的组成
- package.xml文件，它提供了关于包的源信息。
- CMakeList.txt文件，
- 每个包独立拥有自己的文件夹，这意味着没有嵌套的包和多个包使用同一个目录。
- 包的主要结构
```
my_package/
  CMakeLists.txt
  package.xml
```
# catkin工作区中的包结构
```
workspace_folder/        -- WORKSPACE
  src/                   -- SOURCE SPACE
    CMakeLists.txt       -- 'Toplevel' CMake file, provided by catkin
    package_1/
      CMakeLists.txt     -- CMakeLists.txt file for package_1
      package.xml        -- Package manifest for package_1
    ...
    package_n/
      CMakeLists.txt     -- CMakeLists.txt file for package_n
      package.xml        -- Package manifest for package_n
```
# 创建catkin包
## 首先建立工作区，如果没有将ROS全局设置的脚本加入.bashnrc文件的话先手动添加
```
source /opt/ros/melodic/setup.bash
```
## 正式创建工作区
```
mkdir -p ~/catkin_ws/src
cd ~/catkin_ws/
catkin_make
```
## 现在使用catkin_create_pkg 脚本创建一个新的包，并命名为'beginner_tutorials，依赖于std_msgs,roscpp,rospu:
```
catkin_create_pkg beginner_tutorials std_msgs rospy roscpp
```
catkin_create_pkg的用法：
```
catkin_create_pkg <包名> [依赖1] [依赖2] [依赖3]
```
# 创建catkin工作区并获取设置文件
具体命令见上一条,cd进入文件夹后使用命令：
```
catkin_make
```
添加工作区之你的ROS环境
```
. ~/catkin_wa/devel/setup.bash
```
# 包的依赖
## 一阶依赖（直接依赖）
创建包文件时所引用的依赖便是一阶依赖，我们可以使用rospack工具来查看它们：
  ```
  rospack depends1 beginner_tutorials
  ```
  ```
    roscopp
    rospy
    std_msgs
  ```
  可以看出，执行命令后系统列出了我们指定的包文件的依赖
  当然，这些依赖信息也存储在package.xml文件中：
  ```
  roscd beginner_tutorials
  cat package.xml
  ```
  ```
    <package format="2">
    ...
      <buildtool_depend>catkin</buildtool_depend>
      <build_depend>roscpp</build_depend>
      <build_depend>rospy</build_depend>
      <build_depend>std_msgs</build_depend>
    ...
  </package>
  ```
## 间接依赖
很多情况下，一个依赖可能也会有它自己的依赖，例如，我们在创建beginner_tutorial时的依赖有rospy，而rospy的依赖又有genpy，roscpp等。
```
rospack depends1 rospy
```

```
  genpy
  roscpp
  rosgraph
  rosgraph_msgs
  roslib
  std_msgs
```
当然我们也可以列出所有的依赖
```
rospack depends beginner_tutorials
```
# 自定义你自己的包文件
## 自定义package.xml
###description tag
首先更新description tag：
```
 <description>The beginner_tutorials package</description>
```
这个可以任意编辑，但是你应该填入跟这个包文件相关的信息。
### maintainer tags
```
  <!-- One maintainer tag required, multiple allowed, one person per tag --> 
  <!-- Example:  -->
  <!-- <maintainer email="jane.doe@example.com">Jane Doe</maintainer> -->
  <maintainer email="user@todo.todo">user</maintainer>
```
维护者的联系方式
### license tags
发布代码依据的许可证
###dependencies tags
程序包的依赖
```
  <!-- The *_depend tags are used to specify dependencies -->
  <!-- Dependencies can be catkin packages or system dependencies -->
  <!-- Examples: -->
  <!-- Use build_depend for packages you need at compile time: -->
  <!--   <build_depend>genmsg</build_depend> -->
  <!-- Use buildtool_depend for build tool packages: -->
  <!--   <buildtool_depend>catkin</buildtool_depend> -->
  <!-- Use exec_depend for packages you need at runtime: -->
  <!--   <exec_depend>python-yaml</exec_depend> -->
  <!-- Use test_depend for packages you need only for testing: -->
  <!--   <test_depend>gtest</test_depend> -->
  <buildtool_depend>catkin</buildtool_depend>
  <build_depend>roscpp</build_depend>
  <build_depend>rospy</build_depend>
  <build_depend>std_msgs</build_depend>
```
build_tool创建包文件的工具
build_depend创建包文件使用的依赖
### 去除注释后的package.xml
```
<?xml version="1.0"?>
<package format="2">
  <name>beginner_tutorials</name>
  <version>0.1.0</version>
  <description>The beginner_tutorials package</description>

  <maintainer email="you@yourdomain.tld">Your Name</maintainer>
  <license>BSD</license>
  <url type="website">http://wiki.ros.org/beginner_tutorials</url>
  <author email="you@yourdomain.tld">Jane Doe</author>

  <buildtool_depend>catkin</buildtool_depend>

  <build_depend>roscpp</build_depend>
  <build_depend>rospy</build_depend>
  <build_depend>std_msgs</build_depend>

  <exec_depend>roscpp</exec_depend>
  <exec_depend>rospy</exec_depend>
  <exec_depend>std_msgs</exec_depend>

</package>
```
### 自定义CMakeLists.txt
后面详细介绍
