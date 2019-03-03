# Kubernetes

## Installation on Ubuntu 18.04 AMD64

```

#apt-get update -y && apt-get upgrade -y


curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -
cat <<EOF >/etc/apt/sources.list.d/kubernetes.list
deb http://apt.kubernetes.io/ kubernetes-xenial main
EOF
apt-get update && apt-get install -y kubelet kubeadm kubectl


#kubeadm init --pod-network-cidr=10.244.0.0/16 --service-cidr=10.96.0.0/12


```
If you get NumCPU Error , use this 

`#kubeadm init --pod-network-cidr=10.244.0.0/16 --service-cidr=10.96.0.0/12 --ignore-preflight-errors=NumCPU`
