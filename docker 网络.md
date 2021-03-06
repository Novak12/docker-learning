### docker network
运行命令docker network ls，可以从结果中看出docker中包含3中网络：bridge,host和none。这些网络是在安装docker时被自动创建的。</br>
可以在创建容器时指定网络设置：</br>
docker run -it --network=none busybox

#### none网络
从字面意思上就可以看出，none就是什么都没有的网络，但是这不禁让人想问它存在的意义是啥呢？</br>
使用场景：
* 应用需要被隔离，对安全性要求高且不需要联网的应用。

#### host网络
连接到host网络的容器容器共享Docker host的网络栈，容器的网络配置将会与host的网络配置完全一致。</br>
使用场景：
* 容器对网络的传输效率较高，但是其带来的弊端就是可能会引起端口的使用冲突，如Host和容器使用了同一个端口。

#### bridge网络
可能我们都会有一个问题：未指定网络是，docker容器使用的是那种类型的网络？</br>
答案是bridge网络，docker在安装时会创建一个名称为docker0的bridge网络，创建的容器默认会挂载在该网络上。</br>
可以通过brtcl show命令来查看该docker0网络</br>

#### user-defined网络
以上三种网络都是自动创建的网络，用户可以根据业务需要创建user-defined网络，docker提供了三种user-defined网络驱动：bridge、overlay和macvlan。overlay和macvlan用于创建跨主机的网络。
