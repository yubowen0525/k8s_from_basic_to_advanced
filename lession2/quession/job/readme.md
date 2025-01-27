# 单一pod计算
创建job对象
```
$ kubectl create -f job.yaml
```

查看pod的状态
```
kubectl describe jobs/pi
```

等待几分钟结束后pod会成为completed状态
```
$ kubectl logs pi-rq5rl
3.141592653589793238462643383279...
```


# 多个pod并行计算
清理job
```
$ kubectl delete -f job.yaml
```

创建job
```
$ kubectl create -f paralle.yaml
```

查看会发现批任务一次启动了两个pod并行计算
```
$ kubectl get pods
NAME       READY     STATUS    RESTARTS   AGE
pi-5mt88   1/1       Running   0          6s
pi-gmcq5   1/1       Running   0          6s
```

当2个任务完成，继续创建2个pod继续工作
```
$ kubectl get pods
NAME       READY     STATUS    RESTARTS   AGE
pi-gmcq5   0/1       Completed   0         40s
pi-84ww8   0/1       Pending   0         0s
pi-5mt88   0/1       Completed   0         41s
pi-62rbt   0/1       Pending   0         0s

$ kubectl get pods
NAME       READY     STATUS    RESTARTS   AGE
pi-gmcq5   0/1       Completed   0         40s
pi-84ww8   0/1       ContainerCreating   0         0s
pi-5mt88   0/1       Completed   0         41s
pi-62rbt   0/1       ContainerCreating   0         0s
```