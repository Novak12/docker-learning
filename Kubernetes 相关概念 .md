#### Kubernetes

##### 1. Prod
prod是kubernetes中最小的管理单元，一个prod中可能包含多个容器，它是一个容器环境下的额“逻辑主机”。</br>
prod是一种相对断站的存在，prod会被安排在节点上，直至节点终止或者被删除，当一个节点死掉后，它上面的prod均会被删除。
