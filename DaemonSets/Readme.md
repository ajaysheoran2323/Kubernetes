## What is DaemonSets:

  1. If you require multiple pod to be scheduled on every node, you have use DaemonSets
  
 
  2. Once you remove any pod, a new pod will not be *rescheduled*
  
By default you will get couple of daemonSets in `kube-system` namespaces. Their pods run on every node..

```
Ajays-MacBook-Pro:DaemonSet ajaykumar$ kubectl get daemonsets --all-namespaces
NAMESPACE     NAME                DESIRED   CURRENT   READY   UP-TO-DATE   AVAILABLE   NODE SELECTOR                 AGE
kube-system   kube-proxy          2         2         2       2            2           beta.kubernetes.io/os=linux   6d1h
kube-system   kube-svc-redirect   2         2         2       2            2           beta.kubernetes.io/os=linux   6d1h
kube-system   omsagent            2         2         2       2            2           beta.kubernetes.io/os=linux   6d1h
```
