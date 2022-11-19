Create a new Pod
====================

## Method 1: launch it directly

This method is **useful to go fast** but it has the drawback to be **limited in terms of options we can pass** to the new Pod.

```bash
kubectl run nginx --image
```

---

## Method 2: launch prepared Pod

This method is **useful to prepare an advanced configuration** for your Pod before launching it. 

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
