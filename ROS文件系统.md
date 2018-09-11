# 概念
首先是文件系统的两个概念：
- 包（Package）是ROS代码的的组织单元，库、可执行文件、脚本或
- 清单（Manifest）是包的描述，定义包之间的依赖关系，并包含了包的其他信息，如版本，维护者，许可证等。
# 工具
- rospack 
```
rospack find 包的名字
```
```
rospack find roscpp
```
- roscd 用法跟Lunux中cd一样，不过可以直接对ROS文件进行操作，十分方便
```
roscd 包名\包名+子文件名
```
切换当前目录到包roscpp中
```
roscd roscpp
```
切换当前目录到包beginner_tutorials下的src目录中
```
roscd beginner_tutorials/src
```
```
roscd log
```
- rosls 用法同ls，不过可以直接对ROS文件进行操作
```
rosls 包名\包名+子文件名
```
- Tab补全
# 总结
ROS的文件系统常用命令跟linux很相似，不过前面加上了ros前缀，方便了开发者对ROS文件的操作。
# 回顾
- rospack = ros + pack(age)
- roscd = ros + cd
- rosls = ros + ls
