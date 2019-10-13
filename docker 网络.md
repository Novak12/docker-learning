### docker network
运行命令docker network ls，可以从结果中看出docker中包含3中网络：bridge,host和none。这些网络是在安装docker时被自动创建的。</br>

#### none网络
从字面意思上就可以看出，none就是什么都没有的网络，但是这不禁让人想问它存在的意义是啥呢？</br>
使用场景：
* 应用需要被隔离，对安全性要求高且不需要联网的应用。

#### host网络

