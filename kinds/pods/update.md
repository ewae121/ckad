Pods
==========

Please visit the [Official documentation](https://kubernetes.io/docs/concepts/workloads/pods/) to get Pod unit definition.

The pod sections are:

* [How to retrieve information](retrieve_information.md)
* [Create a new pod](create.md)

Main Commands
--------------

## Retrieve Pods information

```bash
kubectl get pods
kubectl get pods -o wide
```

|option|description|
|---|---|
| -o wide | display extra information on pods.|

---
## Create and instantiate

### Method 1: launch it directly

This method is useful to go fast but it has the drawback to be limited in terms of options we can pass to the new Pod.

```bash
kubectl run nginx --image
```

### Method 2: launch prepared Pod

This method is useful to prepare an advanced configuration for your Pod before launching it. 

1. Create a YAML file with the new configuration

```bash
kubectl run pod-redis --image=redis --dry-run=client -o yaml > pod-redis.yaml
```

This generates a file [pod-redis.yaml](pod-redis.yaml) 

2. Update the configuration manually

3. Load the new Pod

```bash
kubectl apply -f pod-redis.yaml
```

---
## Update an existing Pod

### Method 1: Recreate the Pod

  The method consists to retrieve the running pod information and to recreate it.

  1. Retrieve current Pod information
  2. Update the desired Pod property
  3. Delete current Pod
  4. Recreate the new Pod

  > Works for all properties.

  ```bash
  kubectl get pod pod-redis -o yaml > pod-redis.yaml
  ```

  * Method 2: Edit the running Pod
    ```bash
    ```
    > Some properties can not be updated this way. But in case of failure a file is saved who can be updated or applied using the first method.


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