# Kubernetes
Kubernetes helps to manage cluster of docker nodes. This is called orchestartion. This is a suitation whereby we have one master node that talks to and controls other nodes(slave nodes)

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

## PODS
A POD provides all the resources needed by a container like cpu, ram etc. container runs inside a pod(like VM)
In every pod there should be one main container and others should be helper container. if we have nginx and mysql they should not be ran on the same pod but on different pod

## Nodes
Nodes contains different pods
## Overlay Network
This is a network that allows nodes communicate through a network while inside the nodes different pods communicate through an internal network


To install Kubernetes in windows
Open powershell as admin and run the enter commands
```
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))

choco install minikube kubernetes-cli -y
```

To check kubctl config
This is located in the home directory

```
cat .kub/config
```

To get nodes
```
kubectl.exe get nodes
```
To create deployment
```
kubectl create deployment hello-minikube --image=k8s.ger.io/echoserver:1.10
```
To expose deployment
```
kubectl expose deployment hello-minikube --type=NodePort --port=8080
```


To get pods
```
kubectl get pod
```

To get deployment
```
kubectl get deployment
```

To check your deployment
```
minikube service hello-minikube
```
This will generate a url you can use to access your minikube

To get svc
```
kubectl get svc
```

To delete a svc
```
kubectl delete svc svc_name
```

To delete a deployment
```
kubectl delete deployment deployment_name
```

To stop the minikube cluster
```
minikube stop
```

To delete minikube
```
minikube delete
```
