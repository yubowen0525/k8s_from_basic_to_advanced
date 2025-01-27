1、k8s集群下创建此pod
```
kubectl apply -f liveness.yaml
```

2、查看此pod的名称
```
kubectl get pods 
```

3、查看当前状态
```
kubectl describe pods test-liveness-exec
```

4、清理pod资源
```
kubectl delete -f liveness.yaml
```