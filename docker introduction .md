### docker
docker是一个开放平台，使开发人员和管理员可以在成为容器的松散隔离的环境中构建映像、交付和运行分布式应用。
<br/>
docker平台使用docker引擎快速构建应用程序，并将其打包为dockerfile格式编写的文件创造的映像(image)，然后在分层容器中部署和运行。
<br/>

#### docker的应用场景
* web应用自动化打包和发布
* 自动化测试和持续集成、发布
* 在服务型环境中部署和调整数据库或其它的后台应用
* 从头编译或者扩展现有的OpenShift或Cloud Foundry平台来搭建自己的PaaS环境

#### docker的架构
docker是一个C/S架构，client通过接口与server进程通信实现容器的构建、运行和发布。client和server可以运行在同一台集群，也可以通过跨主机实现远程通信。

#### 镜像image
Docker镜像就是一个只读的模板，例如：一个镜像可以包含一个完整的操作系统环境，里面仅安装了 Apache 或用户需要的其它应用程序。Docker 提供了一个很简单的机制来创建镜像或者更新现有的镜像，用户甚至可以直接从其他人那里下载一个已经做好的镜像来直接使用。镜像可以用来创建 Docker 容器，一个镜像可以创建很多容器。

#### 仓库repository
仓库（Repository）是集中存放镜像文件的场所。有时候会把仓库和仓库注册服务器（Registry）混为一谈，并不严格区分。实际上，仓库注册服务器上往往存放着多个仓库，每个仓库中又包含了多个镜像，每个镜像有不同的标签（tag）。<br/>
仓库分为公开仓库和私有仓库两种形式，当用户创建了自己的镜像之后就可以使用 push 命令将它上传到公有或者私有仓库，这样下次在另外一台机器上使用这个镜像时候，只需要从仓库上 pull 下来就可以了。

#### 容器Container
Docker利用容器来运行应用，容器是从镜像中创建的实例，它可以被启动、开始、停止、删除。每个容器都是相互隔离的、保证安全的平台。可以把容器看做是一个简易版的 Linux 环境（包括root用户权限、进程空间、用户空间和网络空间等）和运行在其中的应用程序。<br/>
容器的定义和镜像几乎一模一样，也是一堆层的统一视角，唯一区别在于容器的最上面那一层是可读可写的。<br/>
一个运行态容器被定义为一个可读写的统一文件系统加上隔离的进程空间和包含其中的进程。

#### docker与系统进程
docker容器在技术上实现了与宿主机器的进程隔离。

#### docker vs网络
docker虽然可以通过命名空间创建一个隔离的网络环境，但是docker中的服务仍然需要与外界进行联络才能发挥作用。每一个使用 docker run 启动的容器其实都具有单独的网络命名空间，Docker 为我们提供了四种不同的网络模式，Host、Container、None 和 Bridge 模式。<br/>
docker默认的模式为bridge模式（网桥模式）。在这种模式下，除了分配隔离的网络命名空间之外，Docker 还会为所有的容器设置 IP 地址。当 Docker 服务器在主机上启动之后会创建新的虚拟网桥 docker0，随后在该主机上启动的全部服务在默认情况下都与该网桥相连。<br/>
在默认情况下，每一个容器在创建时都会创建一对虚拟网卡，两个虚拟网卡组成了数据的通道，其中一个会放在创建的容器中，会加入到名为 docker0 网桥中。


#### docker挂载点
