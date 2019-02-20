# docker-learning

### 基本指令
* docker info  //返回所有容器和镜像
* docker images //列出所有的镜像
* docker run  //创建并启动容器

* docker run --name bob_the_container -i -t ubuntu /bin/bash  (--name给容器命名。-i保证容器中STDIN是开启的，-t为容器分配一个伪tty终端)
* docker build   //编译docker镜像
* docker commit //将一个docker容器提交为image

### 创建一个docker应用
* 如何通过dockerfile创建一个docker image  <br/>
对于一个项目，首先创建dockerfile
* 如何给docker image设置标签便于引用  <br/>

* 如何运行行的docker image  <br/>

### docker compose
管理多个容器组成一个应用。<br/>

