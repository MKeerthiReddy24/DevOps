### Kubernetes Multi Node Cluster Setup

#### Creating a cluster:
1. Create a cluster using kind
  ```bash
  kind  create cluster —image <latest-kind-kuberntes-image> —name <cluster-name>
  ```
3. Get the info of the cluster
   ```bash
   kubectl cluster-info —context <cluster-name>
   ```
5. Test to ensure you installed  is up-to-date
   ```bash
   kubectl version —client
   ```
6. Get the nodes
  ```bash
    kubectl get nodes
  ```

#### Creating multinode Cluster:

1. A simple configuration for this can be achieved with the following config file[vi config.yaml] contents:
       # three node (two workers) cluster config
	kind: Cluster
	apiVersion: kind.x-k8s.io/v1alpha4
	nodes:
	- role: control-plane
	- role: worker
	- role: worker
2. Create a new cluster with the file we have created
      ```bash
      kind  create cluster —image <latest-kind-kuberntes-image> —name <cluster-name> —config config.yaml
      ```
3. To get the all clusters [ * - represents the current cluster]
       ```bash
       kubectl config get-contexts
       ```
5. To use a cluster 
       ```bash
       kubectl config use-context  <cluster-name>
       ```

