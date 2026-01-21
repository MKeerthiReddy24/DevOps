## Kubernetes Architecture

<img width="728" height="507" alt="image" src="https://github.com/user-attachments/assets/86aded6e-b607-4692-953a-7b328c9b0e59" />

#### Components:
### Master/Control plane Node V/s Worker Node ( Node is nothing but a Virtual machine)
##### Control Plane
Components that take care of All operational and administrative tasks
##### Worker Node
All Work loads run here
##### API Server
User/Client interacts with cluster using APi server.
##### Scheduler
Decides which pod to be scheduled on which node based on different factors
##### Controller Manager
Controller Manager ensures the desired state by running controllers that create/update/delete resources.
##### ETCD Server
Key value database that stores the cluster state and configuration
##### Kubelet 
Node-level agent that helps container management and receives instructions from Api server
##### Kube proxy 
Pod to pod communication

#### Flow:
1. User raises a request to create a Pod. It goes to API Server.
2. Here API server interacts with Etcd to make a entry for the request.
3. API Server sends request to Scheduler to decide a node for creating the pod.
4. Scheduler decides and specifies the node.
5. APi server instructs the kubelet in the worker node to create the pod.
6. kubelet send to API server that pod has been created.
7. API server then tells to ETCD.
