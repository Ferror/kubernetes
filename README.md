# Kubernetes

## Concepts
### Pod
Abstraction on single container, so you will be able to use Docker or Apache technology
### ConfigMap
List of configuration environments
### Secrets
Just like the ConfigMap, but values are base64 pseudo encrypted
### Volumes
Is a space on disk in Cluster, Node, External or Local
### Service
A thing attached to the pod that has its own lifecycle and enables communication between things in Node/Cluster
based on name instead of ip address
#### Internal
It is a default Service. It's type id defined as Cluster IP.
```yaml
spec:
    type: ClusterIP
```
#### External
It is a Service that can be seen from outside the Cluster.
```yaml
spec:
    type: LoadBalancer
```
### Ingress
Load Balancer of requests, so every request goes through Ingress and then to services
### Deployment
You specify configuration where amount of pods of each type should exist 
### StatefulSet
Don't use that
### Namespace
With installation `default` namespace where all Concepts are placed. It is a form of separation in the cluster
