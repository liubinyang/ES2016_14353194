# Lab 5： 安装ROS

#### ROS框架描述
>	ROS（Robot Operating System，下文简称“ROS”）是一个适用于机器人的开源的元操作系统。它提供了操作系统应有的服务，包括硬件抽象，底层设备控制，常用函数的实现，进程间消息传递，以及包管理。它也提供用于获取、编译、编写、和跨计算机运行代码所需的工具和库函数。



#### ROS安装过程

1. **配置ubuntu软件仓库**

   配置Ubuntu 软件仓库(repositories) 以允许 "restricted"、"universe" 和 "multiverse"这三种安装模式。你可以 [按照ubuntu中的配置指南](https://help.ubuntu.com/community/Repositories/Ubuntu)来完成配置。 

   ​


2. **添加sources.list**

   配置你的电脑使其能够安装来自 packages.ros.org的软件包。

   ```
   sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
   ```



3. **添加keys**

   ```
   sudo apt-key adv --keyserver hkp://pool.sks-keyservers.net --recv-key 0xB01FA116
   ```



4. **安装**

   首先，确保你的Debian软件包索引是最新的： 

   ```
   sudo apt-get update
   ```

   ROS中有很多各种函数库和工具，我安装的是桌面完整版，包含ROS、[rqt](http://wiki.ros.org/rqt)、[rviz](http://wiki.ros.org/rviz)、通用机器人函数库、2D/3D仿真器、导航以及2D/3D感知功能。

   ```
   sudo apt-get install ros-jade-desktop-full
   ```



5. **初始化rosdep**

   在开始使用ROS之前你还需要初始化rosdep。rosdep可以方便在你需要编译某些源码的时候为其安装一些系统依赖，同时也是某些ROS核心功能组件所必需用到的工具。 

   ```
   sudo rosdep init
   rosdep update
   ```

   ​

6. **环境配置**

   如果每次打开一个新的终端时ROS环境变量都能够自动配置好（即添加到bash会话中），那将会方便很多： 

   ```
   echo "source /opt/ros/jade/setup.bash" >> ~/.bashrc
   source ~/.bashrc
   ```



7. **安装rosinstall**

   rosintall是ROS中一个独立分开的常用命令行工具，它可以方便让你通过一条命令就可以给某个ROS软件包下载很多源码树。 

   要在ubuntu上安装这个工具，请运行：

   ```
   sudo apt-get install python-rosinstall
   ```



#### 实验感想与心得

​	这一次的实验是在自己的ubunt上安装ROS，根据实验文档上给出的步骤，很顺利的完成了ROS的整个安装过程。同时这一次实验也稍微熟悉了ROS的一些基本概念，熟悉了实验环境。