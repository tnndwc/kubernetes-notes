
## 更新

> [kube-prometheus](https://github.com/coreos/prometheus-operator/tree/master/contrib/kube-prometheus/manifests)


- retention: "8h" (对应 prometheus --storage.tsdb.retention)
- prometheus 、grafana 使用 NFS 存储
- prometheus 和 grafana service 变更 service type: NodePort
- 编辑 alertmanager-secret.yaml 的 [data].[alertmanager.yaml],定制 alertmanager 配置。（Base 64编码）
```yaml
    # 例子
    global:
    smtp_smarthost: "stmpxxxxx.com:25"
    smtp_from: "from@from.com"
    smtp_auth_username: "username"
    smtp_auth_password: "password"

    route:
    repeat_interval: 10s
    receiver: team-X-mails

    receivers:
    - name: "team-X-mails"
    email_configs:
        - to: "to@to.com"
        #require_tls: false
```
- 



