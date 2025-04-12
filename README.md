# Intro-to-Kubernetes
## Container Orchestration
Container orchestration is a process that automates the life cycle of containerized applications resulting in faster deployment, higher availabilty, reduced errors and stronger security. Popular container orchestration tools include Marathon, Nomad, Docker Swarm, Kubernetes.
## Kubernetes
Kubernetes is a highly portable, open source system for automating deployment, scaling and management of containerized applications to deliver high availability and optimal performance of the containerized applications. Kubernetes was developed by google and has become the de facto standard for deploying containerized applications. The benefits of kubernetes include: automated load balancing, self-healing capabilities and seamless rolling updates.
A deployment of kubernetes is called a kubernetes cluster. A kubernetes cluster is a cluster of nodes that runs containerized applications. Each cluster has one master node, the kubernetes control plane and one or more worker nodes.
A kubernetes control plane maintains the intended state of the cluster by making decisons about the cluster. Example of decision made by the control plane is scheduling workload. It detects and responds to events in the cluster. Example of responding to an event is creating new resources when an application is being deployed.
User applications run on NODES. Nodes are created by cloud providers. This allows kubernetes to run on a variety of infrastructures. The nodes are managed by the control plane. 
Pods are the fundamental deployment units in kubernetes that encapsulates one or more closely related containers that share the same network namespace, storage and set of specifications.
Control plane components are:
API Server: it intercepts RESTful calls from users, developers, administrators etc, validates and processes them. It reads the cluster's current state from the etcd and after a calls execution, it saves the resulting state of the cluster in the etcd.
Scheduler: it assigns new workload objects such as pods encapsulating containers to worker nodes
Controller Managers: it regulates the state of the kubernetes cluster. It compares the desired state gottrn fromt he object's configuration data of the cluster to its current state gotten from the etcd via the API server. 
etcd: it is a strongly consistent, distributed key-value data store used to persist a kubernetes cluster's state. New data is written to the data store only by appending to it, data is never replaced in the data store. Obsolete data is compacted or shredded periodically to minime the size of the data store. Only the API server is able to communicte with the etcd data store.
A worker node has the following components:
Container runtime: in order to manage a container's lifecycle, kubernetes requires a container runtime on the node where a pod and its containers are to be scheuled.
Node Agent; kubelet: it is an agent running on each node. It receives pod definitions from the API server and interacts with the container runtime on the node to run containers associated with the pod.
Proxy; kube-proxy: it is the network agent that runs on each node. It is responsible for dynamic updates and maintenance of all networking rules on the node.
## Minikube
It is one of the most flexible and popular methods to run an all-in-one or a multi node local  kubernetes cluster directly on local workstations.
The minikube PROFILE stores the specifications of our cluster. The minikube profile list allows us to view the status of our clusters in a table formatted output. It provides the info such as profile name, isolation driver, container runtime, kubernetes version, private IP, status of the cluster - running or stopped, the port that exposes the API server to the control plane components, agents and clients which is 8443.
### MINIKUBE COMMANDS
1. minikube start: it starts the cluster.
2. minikube status: it shows the minikube cluster running, the contorl plane, the host and the kubelet node agent.
![Image](https://github.com/user-attachments/assets/501d0545-d1f7-4064-b150-5694e8033571)
3. minikube profile profile-name: switching to another profile. The active marker is then set to the new cluster.
4. minikube stop: it stops the minikube but preserves the configuration and our work.
5. To customise a cluster use the command : minikube start --driver=docker -n 2 \ --container-runtime=cri-o \ --kubernetes-version=v1.27.12 -p minidock
6. minikube node list: it shows the lost of nodes and their IP addresses.
You can access a running cluster through:
Command line interface
Web based user interface from a web browser
APIs from CLI or programmatically
kubectl is the kubernetes command line interface used to deploy applications, manage and configure kubernetes resources.
The kubernetes dashboard provides a web based user interface to interact with a kubernetes cluster to manage resourses and containerized applications.
KUBECTL
The kubectl command line interface is used to interact with resources in the cluster, deploy applications, manage dependencies, terminate applications when no longer needed.
minikube addons list command give you the list of addons enabled or disabled.
minikube dashboard command opens the dashboard in the default browser on your laptop. 
To access the kubernetes cluster, the kubectl client has to interact with the API server running on the control plane node, for this to happen the kubectl client needs the control plane endpoint and appropriate credentials, these can be found in the kubectl configuration file which is created while minikube is started. You can use the command kubectl config view to view this info.
