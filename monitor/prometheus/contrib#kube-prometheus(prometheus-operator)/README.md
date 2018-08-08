# 使用 prometheus 监控 kubernetes 集群

> 本教程使用 [kube-prometheus](https://github.com/coreos/prometheus-operator/tree/master/contrib/kube-prometheus) 创建 prometheus 集群。

### 1.创建
```sh
kubectl create  -f manifests/
```

⚠️ 在创建过程中如果遇到类似这样的错误：
```
no matches for kind "ServiceMonitor" in version "monitoring.coreos.com/v1"
```
使用下面的 delete 操作重来一遍即可😷



### 2.删除
```sh
kubectl delete  -f manifests/
```
⚠️ 删除过程 kubernetes 需要“回收”创建的资源，所以，即便命令执行完成，可能有些资源还在被占用。
因此，执行 delete 命令后，如果立即再 create，可能会提示：
```
unable to create new content in namespace monitoring because it is being terminated
```

### 3.存储
(更新中...)



### 资料：
>[API Docs](https://github.com/coreos/prometheus-operator/blob/24f98e7df9fac7bff8646b9fec89d57b44dbd1d4/Documentation/api.md)

