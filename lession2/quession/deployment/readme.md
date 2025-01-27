# 水平扩展
部署
```
kubectl apply -f demo.yaml --record
```

扩展至4副本
```
$ kubectl scale deployment nginx-deployment --replicas=4
deployment.apps/nginx-deployment scaled
```


# 平滑升级

```
$ kubectl edit deployment/nginx-deployment
... 
    spec:
      containers:
      - name: nginx
        image: nginx:1.9.1 # 1.7.9 -> 1.9.1
        ports:
        - containerPort: 80
...
deployment.extensions/nginx-deployment edited
```

# 回滚

部署
```
kubectl apply -f demo.yaml
```

设置一个不存在的镜像
```
$ kubectl set image deployment/nginx-deployment nginx=nginx:1.91
deployment.extensions/nginx-deployment image updated
```

查看rs状态，发现整体阻塞不再进行
```
$ kubectl get rs
NAME                          DESIRED   CURRENT   READY   AGE
nginx-deployment-1764197365   2         2         2       24s
nginx-deployment-3167673210   0         0         0       35s
nginx-deployment-2156724341   2         2         0       7s
```

回滚操作
```
$ kubectl rollout undo deployment/nginx-deployment
deployment.extensions/nginx-deployment
```

