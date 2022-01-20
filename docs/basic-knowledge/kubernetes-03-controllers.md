
## Controllers

### Deployments

部署表示用户对Kubernetes集群的一次更新操作。部署是一个比RS应用模式更广的API对象，可以是创建一个新的服务，更新一个新的服务，也可以是滚动升级一个服务。
滚动升级一个服务，实际是创建一个新的RS，然后逐渐将新RS中副本数增加到理想状态，将旧RS中的副本数减小到0的复合操作；这样一个复合操作用一个RS是不太好描述的，所以用一个更通用的Deployment来描述。
以Kubernetes的发展方向，未来对所有长期伺服型的的业务的管理，都会通过Deployment来管理。


Kubernetes 1.2后引入，目的是为了更好的解决Pod的编排问题。因此`Deployment`内部使用了`Replica Set`来实现，可以把它看做`Replication Controller(RC)`的升级。
Deployment相对于RC最大升级是可以随时知道当前Pod部署的进度。因为部署一个Pod需要一个连续变化的部署过程，而最终部署成功。

Deployment使用场景：

- 创建一个Deployment对象来生成对应的Replica Set并完成Pod的创建过程。
- 简称Deployment的状态来看部署动作是否完成（实际上就是Pod副本数量是否达到了预期的值）
- 更新Deployment以创建新的Pod（例如镜像升级）
- 如果当前的Deployment不稳定，则回滚到一个早先的Deployment版本
- 挂起或恢复一个Deployment


### CronJobs
### Jobs
### Replica Sets
### Daemon Sets

DaemonSet能够让所有（或者一些特定）的Node节点运行同一个pod。当节点加入到kubernetes集群中，pod会被（DaemonSet）调度到该节点上运行，当节点从kubernetes集群中被移除，被（DaemonSet）调度的pod会被移除，如果删除DaemonSet，所有跟这个DaemonSet相关的pods都会被删除。

### Stateful Sets
### Replication (Controller (RC)) 副本控制器


定义了一个期望的场景（某个Pod）的副本数量在任意时刻都符合某个预期值。包含以下属性：
- Pod期待的副本数（replicas）
- 用户筛选目标Pod的Label Selector
- 当Pod副本数量低于某预期数量的时候，用于创建新Pod的Pod模板
