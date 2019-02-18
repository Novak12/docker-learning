# docker-learning

### 基本指令
* sudo docker info  //返回所有容器和镜像

* sudo docker run  //创建并启动容器

* sudo docker run --name bob_the_container -i -t ubuntu /bin/bash  (--name给容器命名。-i保证容器中STDIN是开启的，-t为容器分配一个伪tty终端)
* sudo docker build   //编译docker镜像
* sudo docker commit //将一个docker容器提交为image

### 创建一个docker应用
* 如何通过dockerfile创建一个docker image  <br/>
对于一个项目，首先创建dockerfile
* 如何给docker image设置标签便于引用  <br/>

* 如何运行行的docker image  <br/>
