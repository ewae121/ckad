Pods
==========

Main Commands
--------------

## Create and instantiate

* Method 1: launch it directly

This method is useful to go fast but it has the drawback to be limited in terms of options we can pass to the new Pod.

```bash
kubectl run nginx --image
```

* Method 2: launch prepared Pod

This method is useful to 

  1. Create YAML file with the new configuration
```bash
kubectl run redis-pod --image=redis --dry-run=client -o yaml > redis-pod.yaml
```

This generates a file as follows:

```yaml
apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: null
  labels:
    run: pod-redis
  name: pod-redis
spec:
  containers:
  - image: redis
    name: pod-redis
    resources: {}
  dnsPolicy: ClusterFirst
  restartPolicy: Always
status: {}
```
  2. Update the configuration manually

  3. Load the new Pod

```bash
kubectl apply -f pod-redis.yaml
```


* Retrieve Pods information

```bash
kubectl get pods
kubectl get pods -o wide
```

* Update an existing Pod

  * Method 1: Recreate the Pod
    1. Retrieve current Pod information
    2. Update the desired Pod property
    3. Delete current Pod
    4. Recreate the new Pod
    > Works for all properties.
    ```bash
    kubectl get pod
    ```
  * Method 2: Edit the running Pod
    ```bash
    ```
    > Some properties can not be updated this way. But in case of failure a file is saved who can be updated or applied using the first method.

