## Kubernetes Services - ClusterIP vs NodePort vs Loadbalancer vs External

#### Kubernetes Service
A Service in Kubernetes provides a stable IP address + DNS name to access a set of Pods.
Because Pods keep changing (deleted, recreated), their IPs change.
Service gives a fixed endpoint to reach those Pods.

#### Types of service:
- ClusterIP (Default)
- NodePort
- LoadBalancer
- ExternalName
- Headless Service

#### ClusterIP
Its used for internal access(microservices calling each other) i.e to expose the service inside the cluster.
#### Nodeport
Exposes service externally using <NodeIP>:<NodePort>.Port range: 30000–32767
#### LoadBalancer
Exposes service externally using a cloud load balancer.
#### ExternalName
Maps a Kubernetes service to an external DNS name. No selector, no proxying. Redirecting to services outside the cluster
#### Headless Service
Does not give a ClusterIP.Used when you need pod IPs directly.
* Common in:
- StatefulSets
- Databases like Cassandra, Kafka
