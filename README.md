# untrunc中文说明文档
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

●`  ./configure`配置文件

●`  make`编译

●`  apt-get install yasm`这条命令是针对上面编译命令的，如果你看到nasm/yasm not found的报错提示，请使用这条命令安装yasm再执行上面的make命令，没有请忽视这条命令

●`  cd ..`返回上一级目录（一定要确保在/home/YourUserName/untrunc-master目录下才能进行下面的编译操作）

●`  g++ -o untrunc -I./libav-12.3 /home/YourUserName/untrunc-master/file.cpp /home/YourUserName/untrunc-master/main.cpp /home/YourUserName/untrunc-master/track.cpp /home/YourUserName/untrunc-master/atom.cpp /home/YourUserName/untrunc-master/mp4.cpp -L./libav-12.3/libavformat -lavformat -L./libav-12.3/libavcodec -lavcodec -L./libav-12.3/libavresample -lavresample -L./libav-12.3/libavutil -lavutil -lpthread -lz -lbz2 -llzma -lX11 -lvdpau`

**进入到最重要的环节了，我在安装的过程中就是在编译源码这一步出现好多问题从而走了不少弯路，比如相对路径报错提示文件不存在，这里需要修改成*绝对路径* 的有5个后缀为cpp的文件，其次就是末尾的参数没有设置，作者默认参数只添加了-lpthread -lz，但是我在编译的时候几乎全都用到了。。。具体参数设置请到作者那里查看**

## 使用
●`  cd /home/YourUserName/untrunc-master`进入到untrunc-master文件夹

●`  ./untrunc /home/YourUserName/good.mp4 /home/YourUserName/bad.mp4`根目录下的good.mp4是用来做参照物的，最好和损坏的视频格式、分辨率、编码一致，然后bad.mp4就是你需要修复的视频文件,最后命令结束后会生成文件名为bad.mp4_fixed.mp4的修复文件

●  wait and enjoy!


