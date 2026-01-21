## Kubernetes Architecture

<img width="735" height="511" alt="image" src="https://github.com/user-attachments/assets/c846166c-5653-4f70-971d-eb5f1b87d457" />

#### Components:
### Master/Control plane Node V/s Worker Node ( Node is nothing but a Virtual machine)
##### Control Plane: Components that take care of All operational and administrative tasks
##### Worker Node: All Work loads run here
### API Server
##### User/Client interacts with cluster using APi server.
### Scheduler
##### Decides which pod to be scheduled on which node based on different factors
### Controller Manager
##### Controller Manager ensures the desired state by running controllers that create/update/delete resources.
### ETCD Server
##### Key value database that stores the cluster state and configuration
### Kubelet 
##### Node-level agent that helps container management and receives instructions from Api server
### Kube proxy 
##### Pod to pod communication
