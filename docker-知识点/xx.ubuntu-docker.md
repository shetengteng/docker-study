- 3台虚拟机
- 安装docker
```sh
sudo apt-get remove docker docker-engine docker.io containerd runc
# 更新软件源
sudo apt-get update
# 安装所需依赖
sudo apt-get -y install apt-transport-https ca-certificates curl software-properties-common
# 安装 GPG 证书
curl -fsSL http://mirrors.aliyun.com/docker-ce/linux/ubuntu/gpg | sudo apt-key add -
# 新增软件源信息
sudo add-apt-repository "deb [arch=amd64] http://mirrors.aliyun.com/docker-ce/linux/ubuntu $(lsb_release -cs) stable"
# 再次更新软件源
sudo apt-get -y update
# 安装 Docker CE 版 sudo apt-get -y install docker-ce
sudo apt-get -y install docker-ce docker-ce-cli containerd.io
```

- 安装kubeadm

```sh
apt-get update  
apt-get install -y kubelet kubeadm kubectl
```

- 提前拉取镜像

```sh
sudo kubeadm config images pull
```

- 启动master节点

```sh
sudo kubeadm init --pod-network-cidr 172.100.0.0/16 --apiserver-advertise-address 192.168.1.135


kubeadm join 192.168.1.135:6443 --token oqbvi0.r13woqfy06o68pv0 \
    --discovery-token-ca-cert-hash sha256:c3604473e7a93b1cc9895efcb0bed94a991b42c99fb748ea66fd93169cac1291 
```

- 查看状态

```sh
root@ubuntu:/opt/k8s# kubectl get nodes
NAME         STATUS     ROLES    AGE    VERSION
k8s-master   NotReady   master   2m7s   v1.18.1
```

- 关于面板

```sh
# 部署
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.0.0-rc7/aio/deploy/recommended.yaml
# 启动
kubectl proxy
# 访问
http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/
```



```sh
wget https://raw.githubusercontent.com/kubernetes/dashboard/v2.0.0-rc7/aio/deploy/recommended.yaml
```



