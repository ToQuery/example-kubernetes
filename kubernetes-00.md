


#### 1. Master（节点）

Master 节点是 Kubernetes 集群的控制节点，负责整个集群的管理和控制

- Kubernetes API Server (kube-apiserver)：提供HTTP Rest 接口的服务，Kubernetes所有资源的增、删、查、改操作的入口
- Kubernetes Controller Manager （kube-controller-manager）：Kubernetes所有资源对象的自动糊控制中心
- Kubernetes Scheduler （kube-scheduler）：负责资源调度（Pod调度）

#### 2. Node（节点）

集群中的工作负载节点（从节点），较早的版本叫做Minion，当Node宕机会被Master自动转移到其他节点

- kubelet： 负责Pod对应容器的创建、启停，与Master节点协作，实现集群管理的基本功能
- kube-proxy：实现Kubernetes Service的通信与负载均衡机制
- Docker Engine （docker）：Docker引擎，负责本机的容器创建和管理

#### 3. Pod


Pod 是 Kubernetes 最基本的部署调度单元。每个 Pod 可以由一个或多个业务容器和一个根容器(Pause 容器)组成。一个 Pod 表示某个应用的一个实例

> Pause容器主要有两个原因，
> 1. 用于确定容器死亡还是整体死亡。
> 2. Pod里的多个业务共享Pause容器的IP，共享Pause容器挂载的Volume

每个Pod都分配了唯一的IP地址（PodIP），一个Pod里的多个容器共享Pod IP地址。




## 4. Label（标签）

Label（标签）是一个key=value的键值对，可以设置多个，附加到各种资源对象上。

- 版本标签：rerlease:stable,rerlease:beta
- 环境标签：
- 架构标签：
- 分区标签：
- 质量管控标签：

说到标签，不得不提到标签选择器，标签选择器类似于SQL、JQuery的选择器，包括常用的`=`,`!=`,`in`,`not in`,`and`关键字。

## 12. Annotation（注解）

与Label类似，使用key/value键值对形式进行定义。严格的命名规则。

## 11. Namespace（命名空间）

Namespace（命名空间）在很多情况下用于实现多租户的资源隔离。
