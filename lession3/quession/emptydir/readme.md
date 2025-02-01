```
kubectl apply -f emptydir-demo.yaml
```

```
kubectl exec -it emptydir-demo -c writer -- ls -al /cache

kubectl exec -it emptydir-demo -c reader -- ls -al /cache
```