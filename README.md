# Kubernetes

## Concepts
### Pod
Abstraction on single container, so you will be able to use Docker or Apache technology
### ConfigMap
List of configuration environments
### Secrets
Just like the ConfigMap, but values are base64 pseudo encrypted
### Volumes
Is a space on disk in Cluster, Node, External or Local. They require admin managements, as they are not managed
by Kubernetes and are treated more like an interface.

#### Persistent Volume (PV)
Like a RAM or CPU just to store data. PV cannot be namespaced.

#### Persistent Volume Claim (PVC)
It's like a requirement, that can be meet by the Persistent Volume. Pod requests ex. 10GB of storage via PVC,
then these request can be meet by PV of 10GB storage. PVC must be in the same namespace as Pod.

#### Storage Class (SC)
Defines persistent storage volumes dynamically

### Service
A thing attached to the pod that has its own lifecycle and enables communication between things in Node/Cluster
based on name instead of ip address
#### ClusterIP
It is a default Internal Service. It's type id defined as Cluster IP.
```yaml
spec:
    type: ClusterIP
```
#### LoadBalancer
It is External Service that can be seen from outside the Cluster.
```yaml
spec:
    type: LoadBalancer
```
#### Headless
Used when the same nodes have to communicate within.
#### NodePort

LoadBalancer > NodePort > ClusterIP > Headless

### Ingress
Load Balancer of requests, so every request goes through Ingress and then to services
### Deployment
You specify configuration where amount of pods of each type should exist 
### StatefulSet

It's a Deployment for Stateful Applications like Databases. Yet, databases requires much more attention that StatefulSet
proposes therefore the best practice is to use dedicated managed database. Without it, you have to take care of backups
and data sync.

### Namespace
With installation `default` namespace where all Concepts are placed. It is a form of separation in the cluster
