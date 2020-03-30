# untrunc中文说明文档
感谢作者提供的项目让我的视频起死回生：
https://github.com/ponchio/untrunc
## 安装（On Ubuntu16.04）
### 推荐先在终端敲上`  sudo su`的命令进入管理员模式
●`  wget https://github.com/ponchio/untrunc/archive/master.zip`下载主程序源码

●`  unzip master.zip`解压源码

●`  wget https://github.com/libav/libav/archive/v12.3.zip`下载libav库

●`  mv -f /home/YourUserName/v12.3.zip /home/YourUserName/untrunc-master`这一步是把根目录下载的v12.3.zip移动到untrunc-master目录中，'YourUserName'是你装linux系统的时候设置的用户名，推荐使用绝对路径万无一失，相对路径存在不稳定性，别嫌麻烦，动手敲吧！

●`  cd /home/YourUserName/untrunc-master`进入到untrunc-master目录

●`  unzip v12.3.zip`解压libav库

●`  cd /home/YourUserName/untrunc-master/libav-12.3`进入到liav-12.3目录

●`  ./configure`配置文件

●`  make`编译

●`  apt-get install yasm`这条命令是针对上面编译命令的，如果你看到nasm/yasm not found的报错提示，请使用这条命令安装yasm再执行上面的make命令，没有请忽视这条命令

●`  cd ..`返回上一级目录

●`  g++ -o untrunc -I./libav-12.3 file.cpp main.cpp track.cpp atom.cpp mp4.cpp -L./libav-12.3/libavformat -lavformat -L./libav-12.3/libavcodec -lavcodec -L./libav-12.3/libavresample -lavresample -L./libav-12.3/libavutil -lavutil -lpthread -lz`
