## Kubernetes Architecture

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/c65d8edd-fde1-49ea-8bd3-5ea9692f30e7" />

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
1. You send a request to create a Pod.The API Server receives it.
2. API Server saves the Pod details into etcd (the database).This is the desired state.
3. API Server notifies the Scheduler that a Pod is pending (no node assigned). Scheduler is informed that there is a new Pod that needs a node.
4. Scheduler selects the best node and updates the Pod’s nodeName in the API Server.
5. API Server stores the updated state (with nodeName assigned) in etcd.
6. Kubelet creates the Pod (pulls images, starts containers) and then sends the Pod status back to the API Server.
7. Once done → sends Pod status (Running/Failed/Pending) back to API Server.
8. API Server stores the new Pod status in etcd.

