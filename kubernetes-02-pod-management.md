
## Pod Management

### Pods
### Autoscalers

#### Horizontal Pod Autoscaler (HPA)

Horizontal Pod Autoscaler简称`HPA`，意思是Pod横向自动扩容。主要用于Pod自动扩容属性，与`kubectl scale`命令类似。通过分析RC控制所有目标的Pod的负载变化情况，来确定是否需要针对性的调整目标Pod的副本数量。
有两种方式作为度量指标：


- CPUUtilizationPercentage
- 应用自定义度量指标（RPS，TPS）

> 1. CPUUtilizationPercentage计算方式：目标Pod所有副本自身的CPU利用率的平均值
> 2. CPU利用率：一个Pod吱声的CPU利用率是该Pod当前CPU的使用量除以它的Pod Request的值。例如定义一个Pod的Pod Request为0.4，而当前Pod的CPU使用量为0.2，则它的CPU使用率为50%。

> CPUUtilizationPercentage是1分钟内的平均值，通过Heapster组件获取，因此需要安装这个组件。
>

Kubernetes 1.1后引入（apiVersion:extensions/v1beta1），1.2版本后升级稳定版(apiVersion:Autoscaling/v1)，1.3版本移除旧版本，1.4版本移除旧版本的支持。


### Ingresses


1.2+

### Services

Kubernetes 里每个Service其实就是我们经常提起的微服务架构中的一个“微服务”，Pod、RC等都是为Servie做嫁衣的。

### Endpoints
### Accounts
### Secrets
### Config

1.2 +
