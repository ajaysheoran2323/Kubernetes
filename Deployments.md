# K8s "Deployment"

You should never create naked pod in production environment and always use "Deployments" or "ReplicationController" to run pods


## Deployment

Create a `first-deployment.yaml` file

```
apiVersion: apps/v1beta1
kind: Deployment
metadata:
  # Unique key of the Deployment instance
  name: deployment-example
spec:
  # 3 Pods should exist at all times.
  replicas: 3
  template:
    metadata:
      labels:
        # Apply this label to pods and default
        # the Deployment label selector to this value
        app: nginx
    spec:
      containers:
      - name: nginx
        # Run this image
        image: nginx:1.10
        
 ```
 
 Run `kubectl apply -f first-deployment.yaml`
 
 `kubectl get deployments --all-namespaces`
 `kubectl describe deployment -n default`
 `kubectl delete deployment`
