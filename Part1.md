# K8s class- Part 1:


Once you have your own EKS or GKP or AKS ready, you can run below basic command:
--------------------------------------------------------
To lits all nodes including Master node

`kubectl get nodes` 

```
Ajays-MacBook-Pro:kubernetes ajaykumar$ kubectl get nodes
NAME                       STATUS   ROLES   AGE    VERSION
aks-agentpool-41067869-0   Ready    agent   105m   v1.12.6
aks-agentpool-41067869-1   Ready    agent   105m   v1.12.6
```
--------------------------------------------------------
To list all pods in all namespaces

`kubectl get pods --all-namespaces`

```
Ajays-MacBook-Pro:kubernetes ajaykumar$ kubectl get pods --all-namespaces
NAMESPACE     NAME                                 READY   STATUS    RESTARTS   AGE
kube-system   coredns-754f947b4-lpn99              1/1     Running   0          107m
kube-system   coredns-754f947b4-zgjqx              1/1     Running   0          110m
kube-system   coredns-autoscaler-6fcdb7d64-sx98v   1/1     Running   0          110m
kube-system   heapster-7b66f54b4c-6f4m5            2/2     Running   0          106m
kube-system   kube-proxy-fbmdc                     1/1     Running   0          107m
kube-system   kube-proxy-mrbhh                     1/1     Running   0          107m
kube-system   kube-svc-redirect-t6lgz              2/2     Running   0          107m
kube-system   kube-svc-redirect-v6vfr              2/2     Running   0          107m
kube-system   kubernetes-dashboard-dfbbfd8-vpq78   1/1     Running   0          110m
kube-system   metrics-server-7b97f9cd9-pb9pl       1/1     Running   0          110m
kube-system   omsagent-458vw                       1/1     Running   0          107m
kube-system   omsagent-rs-96b8fd558-669dt          1/1     Running   0          110m
kube-system   omsagent-w9db4                       1/1     Running   0          107m
kube-system   tiller-deploy-6fb6d4777d-rkzns       1/1     Running   0          83m
kube-system   tunnelfront-699db78879-6z8qw         1/1     Running   0          110m
```

