

## Infrastructure

### Nodes
### Volumes

Volume是Pod能够被多个容器访问的共享目录，与Docker的Volume相似，但不能等价。首先，Kubernetes中的Volume定义在Pod上，然后被一个Pod里的多个容器挂载到具体的文件目录下；其次Kubernetes的Volume与Pod的生命周期相同，但与容器的生命周期不相关，当容器终止或者重启时，Volume中的数据也不会丢失。支持多种先进的分布式文件系统（GlusterFS，Ceph）等。


#### Peeesistent Volume

Kubernetes集群中的某个网络存储中对应的一块存储，它与Volume类似，但有以下区别：
- PV只能是网络存储，不属于任何Node，但可以在每个Node上访问。
- PV并不是定义在Pod之上的，而是独立于Pod之外的定义。
- PV目前只有几种类型：GCE Persistent Disks、NFS、RBD、iSCSCI、AWS ElasticBlockStore、GlusterFS等。



### Claims
### Quotas
### Limits
