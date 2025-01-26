1、打包镜像
```
sh build.sh
```

2、运行容器
```
sh start.sh
```

optional：限制只能使用0.1核CPU
```
sh start2.sh
```

3、测试容器
测试普通接口
```
sh test.sh
```

测试for循环接口来验证资源限制的效果
```
sh test2.sh
```

4、清理容器 (注意容器和镜像的概念，只是清理容器)
```
sh clear.sh
```


