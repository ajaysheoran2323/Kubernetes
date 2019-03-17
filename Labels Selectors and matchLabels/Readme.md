# Labels:

Labels are key value pairs that can be used to identify, or group the resources in Kubernetes. In other words, labels can be used to select resources from a list.

To understand this, lets do a lab:

```
apiVersion: v1
kind: Pod
metadata:
  name: example-pod
  labels:
    env: development
spec:
  containers:
  - name: label-example
    image: nginx
    ports:
    - containerPort: 80
```
