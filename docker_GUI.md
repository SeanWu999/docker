## docker 相当于没有显示器的系统，如果在ｄｏｃｋｅｒ上进行可视化，需要配置相应的参数

(1)在主系统里面运行: 

sudo apt-get install x11-xserver-utils

xhost +

这两句的作用是开放权限，允许所有用户，当然包括docker,访问X11 的显示接口

（２）启动docker的时候完整命令如下：

普通启动时: 

docker run -it docker_caffe2 /bin/bash

调用主机ＧＵＩ启动时：

docker run -v /etc/localtime:/etc/localtime:ro -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=unix$DISPLAY -e GDK_SCALE -e GDK_DPI_SCALE -it docker_caffe2 /bin/bash

其中:

-v /tmp/.X11-unix:/tmp/.X11-unix \           #共享本地unix端口

-e DISPLAY=unix$DISPLAY \                    #修改环境变量DISPLAY

-e GDK_SCALE \                               #我觉得这两个是与显示效果相关的环境变量，没有细究

-e GDK_DPI_SCALE \

(3)每次重新开机，需要在本机操作一次

xhost +



参考地址：[Docker_GUI](https://blog.csdn.net/ericcchen/article/details/79253416)

## 在本机亲测有效的命令：
sudo nvidia-docker run -it -v /home/sean/workspace/docker/data:/usr/workspace -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=unix$DISPLAY -e GDK_SCALE -e GDK_DPI_SCALE cathay/openpose:v1.0 /bin/bash

其中：
（1）-v /home/sean/workspace/docker/data:/usr/workspace 
宿主文件夹 /home/sean/workspace/docker/data 
docker目标文件夹 /usr/workspace 

（2）-v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=unix$DISPLAY -e GDK_SCALE -e GDK_DPI_SCALE 操作GUI命令
（3）cathay/openpose:v1.0 docker镜像名字和tag
（4）载入dockre后的启动命令
