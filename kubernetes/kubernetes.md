# Kubernetes (K8s)
[Kubernetes](https://kubernetes.io) is open-source, pluggable, extensible tool used to automate application containers orchestration at scale. K8S was initialy developed by Google.



## Kubernetes Key Concepts
### Scheduling
### Self-Healing
### Auto-Scaling
* Horizontal
* Vertical
* Cluster
### Service Discovery
### Load Balancing
### High Availability

## Kubernetes components
### Control Plane
Orchestration component responsible for the management of K8s components like clusters, nodes, pods, and networking of those things.

__Master Node__  
- API server  
  Communicates with GUI, external API, CLI. Exposes K8s to outside world
- Controller Manager  
  Keeps an eye on whole cluster.
- Scheduler  
  Schedules containers on different nodes based on workload, resources...
- etcd  
  Key - Value storage. Contains state of whole K8s cluster. Source of truth. Can be used to recover whole cluster based on data from here.  

__Worker Nodes__  
- Kubelet  
  Process allowing Nodes talk to each other  
- Kubeproxy  
  Maintains network rules on nodes  
- Pod(s)  
  Each pods has a container. It can have multiple, but typically has one.  
  Has an IP address  
  Is basically a standalone service.  
  
__Configuration__  
  Fed into an API server on master node. Yaml or JSON. Used by controlle manager (master node).

### Management Plane
Administration layer. Components admins use to interact with K8s - API, custom resource definition, manifests. 

### Data Plane
Handles traffic layer. Overlay, underlay networks between pods, containers...

## Sources
[What is Kubernetes? (and why you should care) - Containers from the Couch](https://www.youtube.com/watch?v=a2gfpZE8vXY)  
[What is Kubernetes? - F5 DevCentral](https://www.youtube.com/watch?v=F60gzQjElGo)
