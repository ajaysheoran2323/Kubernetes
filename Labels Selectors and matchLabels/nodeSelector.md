# Assigning a pod to particular node


You can constrain a pod to only be able to run on particular nodes or to prefer to run on particular nodes. There are several ways to do this, and the recommended approaches all use label selectors to make the selection. 


## nodeSelector

```
apiVersion: v1
kind: Pod
metadata:
  name: nginx
  labels:
    env: test
spec:
  containers:
  - name: nginx
    image: nginx
    imagePullPolicy: IfNotPresent
  nodeSelector:
    disktype: ssd
    
```
