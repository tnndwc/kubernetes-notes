## 怎样通过修改源码的方式定制部分 prometheus 参数

### 比如修改 `scrape_timeout`、`scrape_interval` 等两个参数

1. 修改源码 `pkg/prometheus/promcfg.go`
```go
        func generateConfig(
            ...
            scrapeInterval := "66s"
            ...
            evaluationInterval := "66s"
            ...
            cfg = append(cfg, yaml.MapItem{
                    Key: "global",
                    Value: yaml.MapSlice{
                            ...
                            {Key: "scrape_timeout", Value: "62s"},
                    },
            })
            ...
```
2. make 编译（关联到 Makefile 部分如下）
```Makefile
        ...
        operator: $(GOLANG_FILES)
            GOOS=linux GOARCH=amd64 CGO_ENABLED=0 go build \
            -ldflags "-X github.com/coreos/prometheus-operator/pkg/version.Version=$(shell cat VERSION)" \
            -o $@ cmd/operator/main.go

        ...

        hack/operator-image: Dockerfile operator
	        docker build -t $(REPO):$(TAG) .
	        touch $@
        ...
````
3. 在 kubernetes 中重新部署 prometheus-operator 和 prometheus 即可生效。(在 prometheus 中即可看到如下 Configuration)
```yaml
        global:
        scrape_interval: 66s
        scrape_timeout: 62s
        evaluation_interval: 66s
        ...
```