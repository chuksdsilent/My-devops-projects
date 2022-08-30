# Kubernetics
Kubernetics helps to manage cluster of docker nodes. This is called orchestartion. This is a suitation whereby we have one master node that talks to and controls other nodes(slave nodes)

## Different orchestration tools
* Docker swarm
* Kubernetics(The most popular)
* Mesosphere Marathon
* AWS ECS&EKS
* Azure Container Service
* Google Container Engine
* CoreOS Fleet
* Openshift


## Features kubernetics provides
* Service discovery and load balancing
* Storage orchestration
* Automated rollouts and rollbacks
* Automatic bin packing
* Self-healing

## Two main components of kubernetics
### Master node or control plane(This controls worker node)
services in Master node
* Api Server
* Scheduler
* Controller Manager
* etcd

### Worker Node(This is where docker engine is running)
services in Worker node
* Kubelet
* Proxy
* Docker Engine

## Master Node
### Kube API Server
Main Hero! Handles all the requests and enables communication across stacks services
component on the master that exposes the Kubernetes API
it is the front-end for the kubernetes control plane
Admins connects to it using kubectl CLI
web Dashboard can be integrated with this API

### ETCD Server
* stores all the information
* consistent and highly available key value store used as kubernetes backing store for all cluster data
* kube API stores retrieves info from it
* Should be backed up regularly
* Stores the current state of everything in the cluster

### Kube Scheduler
* watches newly created pods that have no node assigned and selects a node for them to run on
* factors taken into account for sheduling decisions
* individual and collective resource requirements
* hadware/software/policy constraints
* affinity and anti-affinity specifications
* data locality
* inter-workload interference and deadlines

Controller Manager
* Logically, each controller is a separate process
* To reduce complexity, they are all compiled into single binary and run in a single process
These controllers include:
* Controller: Responsible for noticing and responding when nodes go down.
* Replication Controller: Responsible for maintaining the correct number of pods for every replication controller object in the system.
* Endpoint Controller: Poplulates the Endpoints object(that is, joins services & pods).
* Account & Token Controllers: Create default accounts and API access tokens for new namespace
	
## WORKER NODE
### Kubelet
* An agent that runs on each node in the cluster. it makes sure that containers are running in a pod
* Kube Proxy
* Network proxy that runs on each node in your cluster
* Network Rule

Rules allows network communication to your Pods inside or outside of your cluster
Container Runtime suport several container runtime like
* Docker
* containerd
* cri-o, rklet
* Kubernetes CRI(Container Runtime Interface)

Addons
DNS
Web UI
Container Resource Monitoring
Cluster Level Logging
	
