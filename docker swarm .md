
### Docker Swarm
Docker Swarm包括两个方面：一个企业级的安全集群，一个为服务应用编排引擎。

#### Swarm集群
一个docker swarm集群由多个docker节点组成，这些docker可以是物理服务器、虚拟机或云服务器实例。</br>
前提点：所有的节点都要通过可靠的网络连接。
节点会被分配为管理节点或工作节点【manager和worker】.<br/>
管理节点：负责集群control plane,如监控集群状态和分发任务到工作节点等。</br>
工作节点：接受管理节点分配的任务并执行。</br>

Swarm 的配置和状态信息保存在一套位于所有管理节点上的分布式 etcd 数据库中。该数据库运行于内存中，并保持数据的最新状态。关于该数据库最棒的是，它几乎不需要任何配置，作为 Swarm 的一部分被安装，无须管理。</br>

#### Swarm编排
Swarm 中的最小调度单元是服务(service),当容器被封装在一个服务中时，我们称之为一个任务或一个副本，服务中增加了诸如扩缩容、滚动升级以及简单回滚等特性。

####  搭建Swarm
不包含在任何 Swarm 中的 Docker 节点，称为运行于单引擎（Single-Engine）模式。一旦被加入 Swarm 集群，则切换为 Swarm 模式.</br>
在单引擎模式下的 Docker 主机上运行 :</br>
docker swarm init  // 会将其切换到 Swarm 模式，并创建一个新的 Swarm，将自身设置为 Swarm 的第一个管理节点</br>
