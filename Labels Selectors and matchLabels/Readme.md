# Labels:

Labels are key value pairs that can be used to identify, or group the resources in Kubernetes. In other words, labels can be used to select resources from a list.

To understand this, lets do a lab, create a `sample-pod.yaml` file as below:

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

`kubectl apply -f sample-pod.yaml `

```
kubectl get po
NAME READY  STATUS RESTARTS AGE
example-pod 1/1    Running 0 3m

```


```
kubectl get pod example-pod --show-labels
```
##### Label pod:

`kubectl label pod example-pod tier=backend`

`kubectl label pod example-pod key1=value1 key2=value2 etc=etc`

##### Removing a label:

`kubectl label pod example-pod tier-`

`kubectl get pod example-pod --show-labels`

###### Updating label:

`kubectl label --overwrite pods example-pod env=prod`



Lets create one more pod by editing the above yaml and changing metadata.name to example-pod1. Also we will remove the label from yaml.

```
apiVersion: v1
kind: Pod
metadata:
  name: example-pod1
spec:
  containers:
  - name: label-example
    image: nginx
    ports:
    - containerPort: 80
```

Create a yaml file with above content , lets say `sample-pod1.yaml` and apply it.


`kubectl apply -f sample-pod1.yaml `

`kubectl get pods --show-labels`

### Selection Via Labels(Label Selector)

`kubectl get po --show-labels`

Equality-based requirement (`=`,`==`,`!=`)

`kubectl get pods  -l env=prod`

`kubectl get pods  -l env!=prod`

`kubectl get pods  -l status==offline,status=online`

Set Based Requirement
Label selectors also support set based requirements. In other words, label selectors can be use to specify a set of resources.

The supported operators here are `in` , `notin` and `exists` .

`kubectl get pod -l 'env in (prod)'`


### Selection Via Fields(Field Selector)


`kubectl get pod --field-selector metadata.name=example-pod`


### Important:
Selector Supports - Services and ReplicationController
mactLabels Supports - Job, Deployment, Replica Set, and Daemon Set.

#### matchExpressions
  matchExpressions is a list of pod selector requirements. Valid operators include In, NotIn, Exists, and DoesNotExist
