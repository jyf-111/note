# 坎巴拉KSP krpc C++ 服务器客户端部署
推荐高颜值网易云播放器yesplaymusic,编译过程过于无聊
python一行完成安装  
C++需要n天  

本教程需要熟悉KSP cmake vscode或任意IDE编辑器(WSL2 可选)

如不熟悉就直接拿轮子去配置IDE或编辑器环境

轮子:  
mingw编译  
[https://github.com/jyf-111/krpc-mingw](https://github.com/jyf-111/krpc-mingw)  
vs编译  
[https://github.com/jyf-111/krpc-mingw](https://github.com/jyf-111/krpc-mingw)


## 服务器部署通过 ckan 或者 手动安装 (参考其他视频，网上有很多)

## C++客户端部署
### linux部署(WSL2)
参考官方 [https://krpc.github.io/krpc/cpp/client.html](https://krpc.github.io/krpc/cpp/client.html)


1. sudo apt install libasio-dev
2. sudo apt install libprotobuf-dev protobuf-compiler (不用像官方教程一样拉源码编译)
3. 拉krpc-cpp-4.8.0源码,官网提供3种方式configure cmake 和手动安装(前两种安装成功，第三种没试过)
4. 写main.cpp测试  g++ main.cpp -std=c++11 -lkrpc -lprotobuf -pthread (这里linux下要加线程库（官网没说）)
5. 打开KSP KRPC 注意ip和端口

2022/4/5
win + WSL2 测试成功  
WSL2 krpc客户端连接 win krpc服务器成功  
(注意此处 一定是WSL2 因为有独立ip 如果是WSL1的话没有独立ip 和宿主机共享ip和端口 宿主机可以ping localhost访问WSL 但WSL ping宿主机就很麻烦)  

然后vscode 插件连WSL2(或者SSH连) 远程开发很舒服


### windows部署（VS,vscode）

我造的轮子[https://github.com/jyf-111/krpc-mingw](https://github.com/jyf-111/krpc-mingw)


也可以使用vcpkg conan等C++包管理器 
boost-asio可以 asio单独也可
#### vscode + cmake-gui + mingw + protobuf3.6.1 + asio1.12.1(独立版,非boost) + Krpc

全部在管理员状态下运行或安装sudo

1. 安装mingw确保可以跑helloworld
2. 编译protobuf cmake-gui 取消参数Protobuf_BUILD_TEST,取消Protobuf_WITH_ZLIB,确定自己编译的是release,还是debug   

却换到build目录
 make -j 8    
 make install destdir="你想的目录"

protobuf编译结束

3. asio(独立版为headonline)只有头文件没有动态静态库，无需make

4. 编译Krpc
cmake-gui  
参数CMKAE_PRIFIX_PATH 设置为你protobuf 的install目录(帮助cmake找到protobuf include和lib)
proto.exe不在install的目录下 手动指定在build的目录下，或事先加入环境变量
设置CMAKE_CXX_FLAG = -std=c++11 -I 你asio的include目录  
(帮助cmake找到asio)

make -j 8  
make install destdir="你想要的目录"

vscode+code runner配置参考[https://github.com/jyf-111/kprc/tree/master/.vscode](https://github.com/jyf-111/kprc/tree/master/.vscode)

可以把protobuf 的include lib和asio的include拷贝到krpc的include和lib里只维护krpc文件夹，也可以分开来分开链接

并把libkrpc.dll protobuf.dll拷贝到main.cpp目录下
编译运行
2022/4/7测试成功  

#### VS部署
前人编译好的轮子(只适用于VS和mingw g++不通用)
[https://github.com/LRLVEC/krpc-cpp-bin](https://github.com/LRLVEC/krpc-cpp-bin)

直接加include 和lib 

测试VS2022  2022/4/6测试成功

自己编译的话msvc编译器高度图形化不会比mingw困难

提供其他思路:
cygwin和Msys在win下安装krpc可以参考linux

(完)