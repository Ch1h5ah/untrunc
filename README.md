[<font color=red>~~中文说明文档请点击此处~~</font>](#1) | [推荐另外一个作者的版本，安装更简洁，处理速度更快，并且支持Windows平台](#2)

<details><summary><font size=6 color=#c63>关于repo</font></summary><p>今天是2021年3月30日，写下这篇文档已经是去年3月31日的事了，一年过去了，上午我用新系统重新测试了一遍，看着工具的变化，我觉得有必要写点什么</p>
<p>...</p>
<p>去年3月27日晚间发现自己的视频文件出现问题，然后在V2EX看到有人提到untrunc这个工具，于是我开始研究“原作者”的安装说明（当时“新作者”的Windows图形界面版本并不起效，而且没看懂"新作者"的安装说明,所以我放弃了“新作者”的版本），在得知运行环境是Linux操作系统后，就开始搜索如何安装双系统。</p>
<p>于是3月28日的后半夜我都在装系统上踩坑（我忽略了笔记本有两块硬盘，而启动盘只能有一个,以及空闲磁盘的颜色状态须是绿色才符合要求），早上6点扛不住了，电脑没关，就倒床上睡着了，下午1点醒来马上从床上翻起来继续踩坑，搜到一个修改启动引导项的答案直接把我的电脑搞蓝屏了...然而我唯一的U盘被做成Linux系统启动盘了...3月28日晚上7点背着笔记本，骑着共享单车去找修电脑的地方重装系统，再买了一个U盘做PE以防万一。</p>
<p>折腾到3月29日终于装好系统后,又开始在安装untrunc的过程中到处踩坑...当时"原作者"写的安装说明用的是相对路径,需要改成绝对路径才不会报错;第二个就是"原作者"写的安装说明漏掉了'-L./libav-12.3/libavresample -lavresample'这一小段;第三个就是自己装系统时自定义分区,需要在命令行加上额外的参数。这三个问题虽然很小，但天知道我花了多久才发现问题所在。</p>
<P>时间来到3月31日凌晨，经过屡次编译失败后，终于！这一次编译没有报错，我迫不及待地运行起来，大概跑了一个小时——终于成功修复好了！</p>
<p>...</p>
<p>今天我再次用两个版本测试的时候，“新作者”的版本用时3秒左右，“原作者”的版本也能在10秒左右。我更推荐你们用“新作者”Windows图形界面版本，不需要编译，开箱即用。但对我来说，曾经三天三夜废寝忘食的忙碌一件事情，最后盯着滚动的进度条，它停下来的那一刻，并打印出修复成功的信息时，心中的期待、喜悦感、成就感是现在的速度无法比拟的...所以当天我激动的想分享自己的经验，于是便有了这个仓库——写这篇文档的目的就是希望再遇到同样的问题可以少走一些弯路，如果有帮助到你了那便是我的荣幸！</p>
</details>


# Introduction to untrunc

Appreciating author's project to make my video repaired successfully：https://github.com/ponchio/untrunc
### Installing（On Ubuntu 20.04.2.0 LTS）
●`  sudo su`into a root environment

●`  apt upgrade`upgrade apt

●`  apt install yasm make gcc g++`install yasm,etc. as you need

●`  wget https://github.com/ponchio/untrunc/archive/refs/heads/master.zip`download main program source code

●`  unzip master.zip`unzip the source code

●`  wget https://github.com/libav/libav/archive/refs/tags/v12.3.zip`download libav library

●`  mv -f /home/YourUserName/v12.3.zip /home/YourUserName/untrunc-master`in this step,you had better move the libav library to the untrunc-master directory.the 'YourUserName' is what user-name you set when installing linux.bye the way,recommend using the **absolute path** rather than relative path.

●`  cd untrunc-master`change directory to untrunc-master

●`  unzip v12.3.zip`unzip the libav library

●`  cd libav-12.3`change directory to libav-12.3

●`  ./configure`check out the config

●`  make`compiling

●`  cd ..`back to the previous directory and **make sure you are in '/home/YourUserName/untrunc-master' so that you would compile successfully in next step**.

●`  g++ -o untrunc -I./libav-12.3 file.cpp main.cpp track.cpp atom.cpp codec_*.cpp codecstats.cpp codec.cpp mp4.cpp log.cpp -L./libav-12.3/libavformat -lavformat -L./libav-12.3/libavcodec -lavcodec -L./libav-12.3/libavresample -lavresample -L./libav-12.3/libavutil -lavutil -lpthread`

### How to use
●`  cd /home/YourUserName/untrunc-master`change directory to untrunc-master

●`  ./untrunc /home/YourUserName/good.mp4 /home/YourUserName/bad.mp4`the 'bad.mp4' is what you need to restore,and the 'good.mp4' is reference which have the same or similar infomation compared with 'bad.mp4'.finally ,you will get a fixed mp4 file called 'bad.mp4_fixed.mp4' 

●  wait and enjoy!

<h1 id="1">untrunc中文说明文档</h1>

感谢作者提供的项目让我的视频起死回生：https://github.com/ponchio/untrunc
### 安装（On Ubuntu 20.04.2.0 LTS）
●`  sudo su`进入管理员模式

●`  apt upgrade`更新apt

●`  apt install yasm make gcc g++`安装这四个组件（当前系统版本是没有预装这四个组件的，老版本系统也建议检查一遍，以免后面编译报错。国内用户需要先更新软件源才能正常安装，[见下文](#3)）

●`  wget https://github.com/ponchio/untrunc/archive/refs/heads/master.zip`下载主程序源码

●`  unzip master.zip`解压源码

●`  wget https://github.com/libav/libav/archive/refs/tags/v12.3.zip`下载libav库

●`  mv -f /home/YourUserName/v12.3.zip /home/YourUserName/untrunc-master`这一步是把根目录下载的v12.3.zip移动到untrunc-master目录中，'YourUserName'是你装linux系统的时候设置的用户名，推荐使用**绝对路径**万无一失，相对路径存在不稳定性，包括后面编译也要用到**绝对路径**，别嫌麻烦，动手敲吧！

●`  cd untrunc-master`进入到untrunc-master目录

●`  unzip v12.3.zip`解压libav库

●`  cd libav-12.3`进入到libav-12.3目录

●`  ./configure`检测配置文件

●`  make`编译

●`  cd ..`返回上一级目录（一定要确保在/home/YourUserName/untrunc-master目录下才能进行下面的编译操作）

●`  g++ -o untrunc -I./libav-12.3 file.cpp main.cpp track.cpp atom.cpp codec_*.cpp codecstats.cpp codec.cpp mp4.cpp log.cpp -L./libav-12.3/libavformat -lavformat -L./libav-12.3/libavcodec -lavcodec -L./libav-12.3/libavresample -lavresample -L./libav-12.3/libavutil -lavutil -lpthread`

**作者的当前版本对于“相对路径”的支持很友好了，不会再出现之前类似“找不到XXX.cpp”的报错提示了。**

**如果出现“找不到-lxxx”的报错提示，只需删除末尾对应的参数即可（比如作者原文的-lz参数我就没有用到）。**

**如果是自主分区的系统，出现其他报错提示，这种情况只需在最后加上对应的参数即可，具体哪种错误对应哪种参数，请到作者那里查看。**

### 使用
●`  cd /home/YourUserName/untrunc-master`进入到untrunc-master文件夹

●`  ./untrunc /home/YourUserName/good.mp4 /home/YourUserName/bad.mp4`good.mp4是用来做参照物的，最好和损坏的视频格式、分辨率、编码一致，bad.mp4就是你需要修复的视频文件,最后命令结束后会生成文件名为bad.mp4_fixed.mp4的修复文件

●  wait and enjoy!

<h1 id="2">另外一个版本</h1>

作者：https://github.com/anthwlock/untrunc
## Windows用户

Windows用户只需点击[这个链接](https://github.com/anthwlock/untrunc/releases)，下载压缩包，解压后运行"untrunc-gui.exe"这个应用程序即可，如下图所示

![untrunc-gui](img/untrunc-gui.png)

左侧good.mp4是用来做参照物的，最好和损坏的视频格式、分辨率、编码一致，右侧bad.mp4就是你需要修复的视频文件,点击Repair进行修复，最后会生成文件名为bad.mp4_fixed.mp4的修复文件（注意避免出现中文路径）

<h2 id="3">  Linux用户</h2>

国内用户请参考下图先将软件源更新成最佳位置：

![soft&update](img/soft&update.png)

### 安装（On Ubuntu 20.04.2.0 LTS）
●`  sudo su`进入管理员模式

●`  apt upgrade`更新apt

●`  apt install yasm make gcc g++`安装这四个组件（当前系统版本是没有预装这四个组件的，老版本系统也建议检查一遍，以免后面编译报错）

●`  wget https://github.com/anthwlock/untrunc/archive/refs/heads/master.zip`下载主程序源码

●`  unzip master.zip`解压源码

●`  cd untrunc-master`进入到untrunc-master目录

●`  make FF_VER=3.3.9`编译

### 使用
●`  cd /home/YourUserName/untrunc-master`进入到untrunc-master文件夹

●`  ./untrunc /home/YourUserName/good.mp4 /home/YourUserName/bad.mp4`good.mp4是用来做参照物的，最好和损坏的视频格式、分辨率、编码一致，bad.mp4就是你需要修复的视频文件,最后命令结束后会生成文件名为bad.mp4_fixed.mp4的修复文件

●  wait and enjoy!
