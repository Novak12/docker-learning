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
