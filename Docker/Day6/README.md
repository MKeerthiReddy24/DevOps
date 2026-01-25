## Kubernetes Deployment, Replication Controller and ReplicaSet
#### Replica Controller: 
- A legacy one.Rarely used in modern clusters.Replica Controller ensures that all pods are running and up .
- It is replaced by Deployment and Replicaset
#### Replica Set:
- Modern version of ReplicationController. Its purpose is to maintain a stable set of pods running at any given time.
- Usually you defina a deployment and let it manages the Replicasets automatically.
#### Deployment:
- A Deployment manages a set of Pods to run an application workload, usually one that doesn't maintain state.
- A Deployment provides declarative updates for Pods and ReplicaSets.
- A Deployment is the best controller for running apps that do not store data inside the pod.
- It manages pods, handles updates, and ensures the app runs properly.

