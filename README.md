# docker-learning

#### 启动docker服务
systemctl start docker.service
#### 配置开机启动
systemctl enable docker.service

### 基本指令
* docker info  //返回所有容器和镜像
* docker images //列出所有的镜像（top-level）
* docker images -a  //列出所有镜像（top-level和只读层）
* docker run  //创建并启动容器（它包含了两个执行动作，docker create和docker start）
* docker image ls 仓库名+标签名  //列出某个镜像的具体信息

* docker run --name bob_the_container -i -t ubuntu /bin/bash  (--name给容器命名。-i保证容器中STDIN是开启的，-t为容器分配一个伪tty终端)
* docker build   //编译docker镜像
* docker commit //将一个docker容器提交为image
* docker ps //列出所有运行中的容器
* docker ps -a //列出所有的容器
* docker rm *** //删除容器
* docker rmi *** //删除镜像

### 创建一个docker应用
* 如何通过dockerfile创建一个docker image  <br/>
对于一个项目，首先创建dockerfile
* 如何给docker image设置标签便于引用  <br/>
有了dockerfile后，使用docker build将app编译成docker image:<br/>
docker build -t dockerapp:1.0 . 
* 如何运行行的docker image  <br/>
docker run --name=dockerapp -p 5000:80 -d dockerapp:1.0  //80是在dockerfile中设置暴露的接口<br/>
* 查看image的日志 <br/>
docker logs dockerapp
* 如果想启动镜像，并进行交互式操作
docker run -it dockerapp:1.0 bash

### 将docker image推送到dockerhub
1. docker login  //登陆到dockerhub <br/>
2. docker push 用户名/镜像名   （目前测试的结果是：如果名称不符无法push上去，先使用tag命名修改名称）

### docker compose
管理多个容器组成一个应用。<br/>
docker-compose up ---根据docker-compose.yml文件，启动docker image <br/>
docker-compose down --- 停止docker-compose <br/>

docker-compose spa build ---编译某个镜像 <br/>

当运行了docker-compose up后，要进入到某个容器中：<br/>
docker exec -it ams_db bash  //ams_db为容器的名称
