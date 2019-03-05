# Kubernetes

## Installation on Ubuntu 18.04 AMD64

```

#apt-get update -y && apt-get upgrade -y


curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -
cat <<EOF >/etc/apt/sources.list.d/kubernetes.list
deb http://apt.kubernetes.io/ kubernetes-xenial main
EOF
apt-get update && apt-get install -y kubelet kubeadm kubectl
```

#### To initiate master node
`#kubeadm init --pod-network-cidr=10.244.0.0/16 --service-cidr=10.96.0.0/12`

You will get a join token in end. Keep that handy

#### On worker node , paste that token you copied


If you get NumCPU Error , use this 
```
`#kubeadm init --pod-network-cidr=10.244.0.0/16 --service-cidr=10.96.0.0/12 --ignore-preflight-errors=NumCPU`
```

Once you the installation completes, you can run below command on kubenetes Master:

` kubectl get nodes`

Output will be as follows:
```
root@ip-172-31-31-14:/home/ubuntu# kubectl get nodes
NAME              STATUS     ROLES    AGE    VERSION
ip-172-31-31-14   NotReady   master   113s   v1.13.4
```

You can see that `STATUS` is `NotReady`, this is because you need networking also for `kubelet` to handle resources on worker node. 
Run below command to install networking plugin. There are number of networking plugins available and you can choose any of the, We will use `flannel`.

Run below commands on K8s Master to install `flannel` plugin::

```
 #kubectl apply -f https://docs.projectcalico.org/v3.5/getting-started/kubernetes/installation/hosted/etcd.yaml
 #kubectl apply -f https://docs.projectcalico.org/v3.5/getting-started/kubernetes/installation/hosted/calico.yaml
```

Run `kubectl get pods --all-namespaces` on Master node to see if all pods are in running state. Once all are up, run `kubectl get nodes` to see if Master node is `Ready`
```
root@ip-172-31-31-14:/home/ubuntu/kube/yaml# kubectl get nodes
NAME              STATUS   ROLES    AGE   VERSION
ip-172-31-31-14   Ready    master   11m   v1.13.4
```


## Important points to remember 

1. 99.9 %, we will only use `kubectl` command and from Master node only
2. We will never touch Worker node once we join to Master and will work from Master only.
3. `kubeadm init` to initiate master node, `kubeadm join` to join worker node in cluster.
