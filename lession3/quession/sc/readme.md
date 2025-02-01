用户使用声明
```
kubectl get sts -n sase-config 


  volumeClaimTemplates:
  - metadata:
      name: data
    spec: 
      accessModes:
      - ReadWriteOnce
      resources:
        requests:
          storage: 10Gi
      storageClassName: managed-asan-storage
      volumeMode: Filesystem
```

自动创建pod，sc负责创建pvc和pv