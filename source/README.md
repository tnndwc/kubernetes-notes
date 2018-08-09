# 源码

### 安装环境
+ 创建 GOPATH、GOROOT 环境变量
+ 在 GOPATH 环境变量下分别创建 bin、pkg、src 三个目录
+ kubernetes package 是以 k8s.io 开头的，所以，应该创建文件夹 `$GOPATH/src/k8s.io` ，并在该目录下 git clone https://github.com/kubernetes/kubernetes.git


### 源码目录结构
+ 在 Linux 环境下通过 build/release.sh 完成编译
+ kubernetes 源代码放在 pkg 目录下
+ 