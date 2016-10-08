# DOL框架描述
> The distributed operation layer (DOL) is a software development framework to program parallel applications. The DOL allows to specify applications based on the Kahn process network model of computation and features a simulation engine based on SystemC. Moreover, the DOL provides an XML-based specification format to describe the implementation of a parallel application on a multi-processor systems, including binding and mapping.

# DOL安装笔记

####首先要安装一些必要的环境
$   sudo apt-get update
$   sudo apt-get install ant
$   sudo apt-get install openjdk-7-jdk
$   sudo apt-get install unzip

####解压文件
1.新建DOL的文件夹
`$  mkdir dol`

2.将dolethz.zip解压到 dol文件夹中
`$  unzip dol_ethz.zip -d dol`

3.解压systemc
`$  tar -zxvf systemc-2.3.1.tgz`

####编译systemc
1.解压后进入systemc-2.3.1的目录下
`$  cd systemc-2.3.1`

2.新建一个临时文件夹objdir
`$  mkdir objdir`

3.进入该文件夹objdir
`$  cd objdir`

4.运行configure(能根据系统的环境设置一下参数，用于编译)
`$  ../configure CXX=g++ --disable-async-updates`

5.编译
`$  sudo make install`

6.记录当前的工作路径(会输出当前所在路径，记下来，待会有用)
`$  pwd`

####编译DOL
1.进入刚刚dol的文件夹
`$  cd ../dol`

2.修改build_zip.xml文件,找到下面这段话，就是说上面编译的systemc位置在哪里
`<property name="systemc.inc" value="YYY/include"/>`
`<property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"/>`
把YYY改成上页pwd的结果（注意，对于  64位 系统的机器，lib-linux要改成lib-linux64）

3.编译
`$  ant -f build_zip.xml all`
若成功会显示build successful

4.运行第一个例子
进入build/bin/mian路径下
`$  cd build/bin/main`
然后运行第一个例子
`$  ant -f runexample.xml -Dnumber=1`

#实验感想和实验心得
这一次的readme是对第一次实验的一个整体的回顾，复习了DOL的概念、如何安装DO。同时这一次又采用了markdown的方法来写这样一个文档，学习到了一种新的方法，熟悉了实验环境，为接下来的实验做了一个充分的准备。

