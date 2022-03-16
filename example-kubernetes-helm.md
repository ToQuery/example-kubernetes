
## 添加仓库

```shell
helm repo add minio https://charts.min.io
helm repo add kong https://charts.konghq.com
helm repo add elastic https://helm.elastic.co
helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo add grafana https://grafana.github.io/helm-charts
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
helm repo add kubernetes-dashboard https://kubernetes.github.io/dashboard
helm repo add skywalking https://apache.jfrog.io/artifactory/skywalking-helm
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
```

## elasticserch

```shell
helm upgrade --install elasticsearch elasticsearch \
--repo https://helm.elastic.co \
--namespace example-kubernetes --create-namespace \
--set controller.metrics.enabled=true \
--set-string controller.podAnnotations."prometheus\.io/scrape"="true" \
--set-string controller.podAnnotations."prometheus\.io/port"="10254"
```

## nginx

```shell

helm upgrade --install ingress-nginx ingress-nginx \
--repo https://kubernetes.github.io/ingress-nginx \
--namespace example-kubernetes --create-namespace \
--set controller.metrics.enabled=true \
--set-string controller.podAnnotations."prometheus\.io/scrape"="true" \
--set-string controller.podAnnotations."prometheus\.io/port"="10254"

```

## kong

```shell

helm upgrade --install kong kong \
--repo https://charts.konghq.com \
--namespace example-kubernetes --create-namespace \
--set ingressController.installCRDs=false \
--set proxy.type=ClusterIP \
--set proxy.ingress.enabled=true \
--set proxy.ingress.hostname=kong.example-kubernetes.com

```

## minio

```shell
helm upgrade --install minio minio \
--repo https://charts.min.io \
--namespace example-kubernetes --create-namespace \
--set rootUser=root,rootPassword=123456 
```

## postgresql

```shell
helm upgrade --install postgresql postgresql \
--repo https://charts.bitnami.com/bitnami \
--namespace example-kubernetes --create-namespace \
--set global.postgresql.postgresqlPassword=123456
```


## prometheus

```shell
helm upgrade --install prometheus prometheus \
--repo https://prometheus-community.github.io/helm-charts \
--namespace example-kubernetes --create-namespace \
--set server.ingress.enabled=true \
--set server.ingress.hosts=prometheus.example-kubernetes.com
```



