```
kubectl apply -f hostpath-demo.yaml

```


容器上
```
kubectl exec -it hostpath-demo -- sh

ls /mnt
cat /mnt/data.txt

```


宿主机
```
ls /data
cat /data/data.txt
```