# Selectors

Look at the deployment closely

```
apiVersion: apps/v1beta1
kind: Deployment
metadata:
  name: nginx
  labels:
    app: nginx
    tier: backend
spec:
  selector:
    matchLabels:
      app: nginx
  replicas: 2
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx
 ```
 
So, this is kind of confusing. What does the *selector*, *label*, and *matchLabel* do? And why are there multiple nested labels?

So, the first metadata describes the deployment itself. It gives a label for that actual deployment. So, if you want to delete that deployment, you would say `kubectl delete -l app=nginx,tier=backend`


