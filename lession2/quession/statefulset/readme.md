# 拓扑
部署应用
```
kubectl apply -f demo.yaml

kubectl apply -f svc.yaml
```

观察有状态的启动顺序
```
$ kubectl get pods -w -l app=nginx
NAME      READY     STATUS    RESTARTS   AGE
web-0     0/1       Pending   0          0s
web-0     0/1       Pending   0         0s
web-0     0/1       ContainerCreating   0         0s
web-0     1/1       Running   0         19s
web-1     0/1       Pending   0         0s
web-1     0/1       Pending   0         0s
web-1     0/1       ContainerCreating   0         0s
web-1     1/1       Running   0         20s
```


找到服务的具体IP
```
## 获取到coredns的IP地址
kubectl get pods -A -o wide |grep coredns

## 其中web-0.nginx.default.svc.cluster.local就是web-0 pod的地址
## 如果pod发生重启，IP地址会发生变化，而dns并不会变化
nslookup web-0.nginx.default.svc.cluster.local 10.254.167.79
```

删除
```
kubectl delete -f demo.yaml
```

# 存储
```
$ kubectl create -f demo_pv.yaml
$ kubectl get pvc -l app=nginx
NAME        STATUS    VOLUME                                     CAPACITY   ACCESSMODES   AGE
www-web-0   Bound     pvc-15c268c7-b507-11e6-932f-42010a800002   1Gi        RWO           48s
www-web-1   Bound     pvc-15c79307-b507-11e6-932f-42010a800002   1Gi        RWO           48s
```

