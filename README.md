~~中文说明文档请点击此处~~ | [推荐另外一个作者的版本，安装更简洁，处理速度更快，并且支持Windows平台](#2)

# Introduction to untrunc

Appreciating author's project to make my video repaired successfully：
https://github.com/ponchio/untrunc
## Installing（On ubuntu16.04）
### Suggesting input`  sudo su` into administrator mode
●`  wget https://github.com/ponchio/untrunc/archive/master.zip`download main program source code

●`  unzip master.zip`unzip the source code

●`  wget https://github.com/libav/libav/archive/v12.3.zip`download libav library

●`  mv -f /home/YourUserName/v12.3.zip /home/YourUserName/untrunc-master`in this step,you had better move the libav library into the untrunc-master directory.the 'YourUserName' is what user-name you set when installing linux.bye the way,suggesting use the **absolute path** rather than relative path.

●`  cd /home/YourUserName/untrunc-master`enter untrunc-master directory

●`  unzip v12.3.zip`unzip the libav library

●`  cd /home/YourUserName/untrunc-master/libav-12.3`enter libav-12.3 directory

●`  ./configure`check out the config

●`  make`compiling

●`  apt-get install yasm`if you see the error like 'nasm/yasm not found',just install it and then make again. 

●`  cd ..`return the previous directory and **make sure you are in '/home/YourUserName/untrunc-master' so that you would compile successfully in next step**.

●`  g++ -o untrunc -I./libav-12.3 /home/YourUserName/untrunc-master/file.cpp /home/YourUserName/untrunc-master/main.cpp /home/YourUserName/untrunc-master/track.cpp /home/YourUserName/untrunc-master/atom.cpp /home/YourUserName/untrunc-master/mp4.cpp -L./libav-12.3/libavformat -lavformat -L./libav-12.3/libavcodec -lavcodec -L./libav-12.3/libavresample -lavresample -L./libav-12.3/libavutil -lavutil -lpthread -lz -lbz2 -llzma -lX11 -lvdpau`

**in this step,you should look out three points.First,you need change the relative path of five cpp files to absolute path.Second,add '-L./libav-12.3/libavresample -lavresample' in command line.Third,add some flags like "-lbz2 -llzma -lX11 -lvdpau" as you need.**

## How to use
●`  cd /home/YourUserName/untrunc-master`enter the untrunc-master directory

●`  ./untrunc /home/YourUserName/good.mp4 /home/YourUserName/bad.mp4`the 'bad.mp4' is what you need to fix,and the 'good.mp4' is reference which have the same or similar infomation compared with 'bad.mp4'.finally ,you will get a fixed mp4 file called 'bad.mp4_fixed.mp4' 

●  wait and enjoy!

<h1 id="1">untrunc中文说明文档</h1>

感谢作者提供的项目让我的视频起死回生：
https://github.com/ponchio/untrunc
## 安装（On ubuntu16.04）
### 推荐先在终端敲上`  sudo su`的命令进入管理员模式
●`  wget https://github.com/ponchio/untrunc/archive/master.zip`下载主程序源码

●`  unzip master.zip`解压源码

●`  wget https://github.com/libav/libav/archive/v12.3.zip`下载libav库

●`  mv -f /home/YourUserName/v12.3.zip /home/YourUserName/untrunc-master`这一步是把根目录下载的v12.3.zip移动到untrunc-master目录中，'YourUserName'是你装linux系统的时候设置的用户名，推荐使用**绝对路径**万无一失，相对路径存在不稳定性，包括后面编译也要用到**绝对路径**，别嫌麻烦，动手敲吧！

●`  cd /home/YourUserName/untrunc-master`进入到untrunc-master目录

●`  unzip v12.3.zip`解压libav库

●`  cd /home/YourUserName/untrunc-master/libav-12.3`进入到libav-12.3目录

●`  ./configure`检测配置文件

●`  make`编译

●`  apt-get install yasm`这条命令是针对上面两条命令的，如果你看到nasm/yasm not found的报错提示，请使用这条命令安装yasm再执行上面的make命令（国内用户需要先更新软件源才能正常安装yasm，[见下文](#3)）

●`  cd ..`返回上一级目录（一定要确保在/home/YourUserName/untrunc-master目录下才能进行下面的编译操作）

●`  g++ -o untrunc -I./libav-12.3 /home/YourUserName/untrunc-master/file.cpp /home/YourUserName/untrunc-master/main.cpp /home/YourUserName/untrunc-master/track.cpp /home/YourUserName/untrunc-master/atom.cpp /home/YourUserName/untrunc-master/mp4.cpp -L./libav-12.3/libavformat -lavformat -L./libav-12.3/libavcodec -lavcodec -L./libav-12.3/libavresample -lavresample -L./libav-12.3/libavutil -lavutil -lpthread -lz -lbz2 -llzma -lX11 -lvdpau`

**进入到最重要的环节了，我在安装的过程中就是在编译源码这一步出现好多问题从而走了不少弯路，比如相对路径报错提示文件不存在，这里需要修改成*绝对路径* 的有5个后缀为cpp的文件(file.cpp、main.cpp、track.cpp、atom.cpp、mp4.cpp)，另外还需要加上resample库（-L./libav-12.3/libavresample），作者原文代码是没有添加的，其次就是末尾的参数没有设置，作者默认参数只添加了-lpthread -lz，但是我在编译的时候几乎全都用到了。。。具体参数对应哪一种错误请到作者那里查看**

## 使用
●`  cd /home/YourUserName/untrunc-master`进入到untrunc-master文件夹

●`  ./untrunc /home/YourUserName/good.mp4 /home/YourUserName/bad.mp4`bad.mp4就是你需要修复的视频文件,good.mp4是用来做参照物的，最好和损坏的视频格式、分辨率、编码一致，最后命令结束后会生成文件名为bad.mp4_fixed.mp4的修复文件

●  wait and enjoy!

<h1 id="2">另外一个版本</h1>

作者：
https://github.com/anthwlock/untrunc
## Windows用户

Windows用户只需点击[这个链接](https://github.com/anthwlock/untrunc/releases)，下载压缩包，解压后运行"untrunc-gui.exe"这个应用程序即可，如下图所示

![untrunc-gui.exe](https://github.com/Ch1hsah/untrunc/blob/master/3DC501FC3654%7D.png)

<h2 id="3">  Linux用户</h2>

国内用户请参考下图先将软件源更新成最佳位置：

![soft&update](https://github.com/Ch1hsah/untrunc/blob/master/C4LOSPGNWT45.png)

后续出现**“E：无法......”**类似的错误请自行百度或者谷歌
### 推荐先在终端敲上`  sudo su`的命令进入管理员模式
●`  apt update`更新apt

●`  apt-get install yasm`安装yasm

●`  wget https://github.com/anthwlock/untrunc/archive/master.zip`下载主程序源码

●`  unzip master.zip`解压源码

●`  cd untrunc-master`进入到untrunc-master目录

●`  make FF_VER=3.3.9`编译

## 使用
●`  cd untrunc-master`进入到untrunc-master文件夹

●`  ./untrunc /home/YourUserName/good.mp4 /home/YourUserName/bad.mp4`bad.mp4就是你需要修复的视频文件,good.mp4是用来做参照物的，最好和损坏的视频格式、分辨率、编码一致，最后命令结束后会生成文件名为bad.mp4_fixed.mp4的修复文件

●  wait and enjoy!
