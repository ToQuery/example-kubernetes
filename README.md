# example-kubernetes

## kubernetes 基础组件

[TOC]

### Infrastructure

#### Nodes
#### Volumes
#### Claims
#### Quotas
#### Limits

### Pod Management

#### Pods
#### Autoscalers
#### Ingresses
#### Services
#### Endpoints
#### Accounts
#### Secrets
#### Config


### Controllers

#### Deployments
#### CronJobs
#### Jobs
#### Replica Sets
#### Daemon Sets
#### Stateful Sets
#### Replication

### Packages

#### Charts
#### Releases

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



## 7. Horizontal Pod Autoscaler (HPA)

Horizontal Pod Autoscaler简称`HPA`，意思是Pod横向自动扩容。主要用于Pod自动扩容属性，与`kubectl scale`命令类似。通过分析RC控制所有目标的Pod的负载变化情况，来确定是否需要针对性的调整目标Pod的副本数量。
有两种方式作为度量指标：


- CPUUtilizationPercentage
- 应用自定义度量指标（RPS，TPS）

> 1. CPUUtilizationPercentage计算方式：目标Pod所有副本自身的CPU利用率的平均值
> 2. CPU利用率：一个Pod吱声的CPU利用率是该Pod当前CPU的使用量除以它的Pod Request的值。例如定义一个Pod的Pod Request为0.4，而当前Pod的CPU使用量为0.2，则它的CPU使用率为50%。

> CPUUtilizationPercentage是1分钟内的平均值，通过Heapster组件获取，因此需要安装这个组件。
>

Kubernetes 1.1后引入（apiVersion:extensions/v1beta1），1.2版本后升级稳定版(apiVersion:Autoscaling/v1)，1.3版本移除旧版本，1.4版本移除旧版本的支持。

## 8. Service （服务）



## 9. Volume（存储卷）

Volume是Pod能够被多个容器访问的共享目录，与Docker的Volume相似，但不能等价。首先，Kubernetes中的Volume定义在Pod上，然后被一个Pod里的多个容器挂载到具体的文件目录下；其次Kubernetes的Volume与Pod的生命周期相同，但与容器的生命周期不相关，当容器终止或者重启时，Volume中的数据也不会丢失。支持多种先进的分布式文件系统（GlusterFS，Ceph）等。

## 10. Peeesistent Volume

Kubernetes集群中的某个网络存储中对应的一块存储，它与Volume类似，但有以下区别：
- PV只能是网络存储，不属于任何Node，但可以在每个Node上访问。
- PV并不是定义在Pod之上的，而是独立于Pod之外的定义。
- PV目前只有几种类型：GCE Persistent Disks、NFS、RBD、iSCSCI、AWS ElasticBlockStore、GlusterFS等。

## 11. Namespace（命名空间）

Namespace（命名空间）在很多情况下用于实现多租户的资源隔离。

## 12. Annotation（注解）

与Label类似，使用key/value键值对形式进行定义。严格的命名规则。

## Role and ClusterRole

## RoleBinding and ClusterRoleBinding

## ServiceAccount

## ConfigMap


## DaemonSet


## Ingress

