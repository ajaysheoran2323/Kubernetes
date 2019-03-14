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
To get secrets:

`kubectl get secrets`

`kubectl describe secrets/db-user-pass`



