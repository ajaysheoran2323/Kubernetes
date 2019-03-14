## Secrets:

A Secret is an object that contains a small amount of sensitive data such as a password, a token, or a key

### Built-in Secrets

Service Accounts Automatically Create and Attach Secrets with API Credentials


### Creating a Secret Using kubectl create secret

```
# Create files needed for rest of example.

echo -n 'admin' > ./username.txt

echo -n '1f2d1e2e67df' > ./password.txt

kubectl create secret generic db-user-pass --from-file=./username.txt --from-file=./password.txt


```
##### To get secrets:

`kubectl get secrets`

`kubectl describe secrets/db-user-pass`



### Creating a Secret Manually
```
echo -n 'admin' | base64
YWRtaW4=
echo -n '1f2d1e2e67df' | base64
MWYyZDFlMmU2N2Rm
```

```
apiVersion: v1
kind: Secret
metadata:
  name: mysecret
type: Opaque
data:
  username: YWRtaW4=
  password: MWYyZDFlMmU2N2Rm
```

`kubectl create -f ./secret.yaml`


#### Consume a secret in pod


```
apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  containers:
  - name: nginx
    image: nginx
    volumeMounts:
    - name: secretvol
      mountPath: "/mnt/main"
      readOnly: true
  volumes:
  - name: secretvol
    secret:
      secretName: mysecret
```
