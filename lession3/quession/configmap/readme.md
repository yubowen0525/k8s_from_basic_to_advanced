创建configmap
```
kubectl apply -f configmap.yaml
```

创建pod
```
kubectl apply -f pod.yaml
```

进入pod观察
```
kubectl exec -it my-app -- sh

ls -l /etc/config/
cat /etc/config/app.properties
cat /etc/config/db-config.json
```

修改configmap文件后再次apply
```
kubectl apply -f pod.yaml
```

再次执行此命令观察两次的不同
```
ls -l /etc/config/
```