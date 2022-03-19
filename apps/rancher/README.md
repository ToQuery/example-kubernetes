
- https://rancher.com/docs/rancher/v2.6/en/installation/install-rancher-on-k8s/



helm upgrade --install rancher rancher-stable/rancher \
  --namespace cattle-system \
  --set hostname=rancher.example-kubernetes.com \
  --set bootstrapPassword=admin \
  --set ingress-class=nginx

  注意查看Ingress Class 是否为nginx