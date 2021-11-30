# ghost-blog-kubernetes
Deploy Ghost Blog on Google Cloud Kubernetes Engine with SSL

It's very hard to find an exact method of successfully deploying ghost on a kubernetes instance, with easy SSL set up.
These deployment files can be directly used to set up ghost in 5 minutes!

First, deploy the ghost container:

```
kubectl -f apply deployment.yaml
```

Verify the pod status:

```
kubectl get pods
```

Second, deploy the service (load balancer in this case):

```
kubectl -f apply service.yaml
```

Next, deploy the persistant volume (load balancer in this case):

```
kubectl apply -f volume.yaml
```

Now update the container to link it with the volume claim:

```
kubectl apply -f deployment.yaml
```
