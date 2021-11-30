# ghost-blog-kubernetes
Deploy Ghost Blog on Google Cloud Kubernetes Engine with SSL

It's very hard to find an exact method of successfully deploying ghost on a kubernetes instance, with easy SSL set up.
These deployment files can be directly used to set up ghost in 5 minutes!

First, deploy the ghost container:

```
kubectl apply -f deployment.yaml
```

Verify the pod status:

```
kubectl get pods
```

Second, deploy the service (load balancer in this case):

```
kubectl apply -f service.yaml
```

Next, deploy the persistant volume (load balancer in this case):

```
kubectl apply -f volume.yaml
```

Now update the container to link it with the volume claim:

```
kubectl apply -f deployment.yaml
```

SSL Set Up:

We need to create a static ip for ingress. 

```
gcloud compute addresses create blog-static-ip --global
```

Now apply the self managed cert.yaml

```
kubectl apply -f cert.yaml
```

Finally, create an ingress:

```
kubectl apply -f ingress.yaml
```

That's all! Your blog should be set up with SSL certification. 

Note: These are just the deployment files, this is not a tutorial or a guide! This was my approach, but you could do the same with several other methods.
