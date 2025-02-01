```
kubectl apply -f pv.yaml
kubectl apply -f pvc.yaml
kubectl apply -f pod.yaml
```

查看对象状态
```
kubectl get pv
kubectl get pvc

```


容器内查看挂载
```
kubectl exec -it pv-test-pod -- sh

cat /mnt/data.txt

```


清理资源
```
kubectl delete pod pv-test-pod
kubectl delete pvc example-pvc
kubectl delete pv example-pv

```