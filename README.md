# docker
useful docker command line

查看镜像：docker images -a

查看所有正在运行容器：docker ps 

根据ID停止容器：docker stop containerId

通过镜像创建容器：docker run it ubuntu:18.04     (ubuntu是REPOSITORY，18.04是TAG，创建后再启动和进入)

查看所有容器：docker ps -a

停止所有容器：docker stop $(docker ps -a -q)

删除所有容器：docker  rm $(docker ps -a -q)

启动容器：docker start 4691dc97a72c        （后面是id）

进入容器：docker attach 4691dc97a72c       （后面是id）

镜像保存：sudo docker save [镜像REPOSITORY] -o /home/images.tar           (没有中括号)

镜像载入：sudo docker load -i [镜像tar]                                   (没有中括号)

删除容器 docker rm [ID]                 （删除镜像前要先删除容器）

删除镜像 docker rmi [ID]                 （删除镜像前要先删除容器）

