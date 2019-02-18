# docker-learning

### 基本指令
* sudo docker info  //返回所有容器和镜像

* sudo docker run  //创建并启动容器

* sudo docker run --name bob_the_container -i -t ubuntu /bin/bash  (--name给容器命名。-i保证容器中STDIN是开启的，-t为容器分配一个伪tty终端)
* sudo docker build   //编译docker镜像
* sudo docker commit //将一个docker容器提交为image
