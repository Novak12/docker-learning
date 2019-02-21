### build a docker image  --- ubuntu

* 创建一个文件夹 <br/>
  sudo mkdir /var/www/html/docker1
 * 创建一个Dockerfile文件  <br/>
  sudr cd /var/www/html/docker1 <br/>
  sudo vim Dockerfile <br/>
 ```javascript
 //文件内容
FROM ubuntu:latest
MAINTAINER Bourbon Tian "novak12@163.com"
RUN apt-get update
RUN apt-get install -y nginx
RUN echo 'Hi, I am in your container' > /usr/share/nginx/html/index.html
EXPOSE 80
 ```
* 构建镜像 <br/>
 sudo docker build -t="dockertest1/test:v1" .
* 运行 <br/>
 docker run -t -i e98d2c152d1d /bin/bash   //-i后为image的id, /bin/bash 表示启动容器后，启动bash，保持容器有一个进程在运行，不然容器会退出。
