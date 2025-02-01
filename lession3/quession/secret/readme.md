1、 完成configmap的内容创建出pod

2、执行此命令看到容器会挂载一个默认的secret
```
kubectl get secret default-token-9f4hj

kubectl exec my-app ls /var/run/secrets/kubernetes.io/serviceaccount
```