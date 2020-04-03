#### Docker volume
#### 1. docker的文件系统 --- how to work
在docker的文件系统中，一个docker镜像是有由多个文件系统（只读层）叠加而成，当启动一个docker容器时，docker会加载只读层，并在上（镜像栈顶部）增加一个读写层，如果运行中的容器修改了现有的已经存在的文件，那么该文件将会从读写层下的只读层复制到读写层，但是该文件的只读版本依然存在，只是被读写层中该文件的副本所隐藏。当删除该容器，并在此重启该镜像时，之前的更改将会丢失。因此这就带来了在docker容器中数据持久化的问题。

#### 2. Volume概念
Volume的提出就是问了解决docker容器数据的持久化以及容器间如何共享数据的问题。<br/>
Volume就是目录或者文件，它可以绕过docker默认的文件系统，以正常的文件或者目录的形式保存在宿主机上。<br/>
```javascript
docker run -it --name container-test -h CONTAINER -v /data debian /bin/bash
```
在上面的指令中，-v表示声明Volume，/data表示将/data目录挂载到容器中，在host主机上可以直接找到该目录，
```javascipt
docker inspect -f {{.Volumes}} container-test
```
使用上述命令可以找出容器在主机上的Volumn的具体路径。

#### 3. 数据共享
```javascript
docker run -it -h NEWCONTAINER --volumes-from container-test debian /bin/bash
```
如果要授权一个容器访问另一个容器，可使用上述指令，关键词volumes-from。<br/>
值得注意的是，对于初始容器container-test是否运行，新容器都能访问共享的Volumn。
#### 4. Volume删除
```javascript
docker  rm --v
```

#### 管理卷
```javascript
# docker volume create edc-nginx-vol // 创建一个自定义容器卷
# docker volume ls // 查看所有容器卷
# docker volume inspect edc-nginx-vol // 查看指定容器卷详情信息
```
#### 创建使用指定卷的容器
```javascript
# docker run -d -it --name=edc-nginx -p 8800:80 -v edc-nginx-vol:/usr/share/nginx/html nginx
```
-v代表挂载数据卷，这里使用自定数据卷edc-nginx-vol，并且将数据卷挂载到 /usr/share/nginx/html （这个目录是yum安装nginx的默认网页目录）.</br>
如果没有通过-v指定，那么Docker会默认帮我们创建匿名数据卷进行映射和挂载。</br>

#### 清理卷
```javascript
# docker stop edc-nginx // 暂停容器实例
# docker rm edc-nginx // 移除容器实例
# docker volume rm edc-nginx-vol // 删除自定义数据卷
```
