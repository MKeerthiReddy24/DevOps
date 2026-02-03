### Kubernetes Namespace
- A Kubernetes Namespace is a virtual cluster inside a physical cluster.
- It helps isolate resources, limit usage, secure workloads, and organize applications based on teams or environments.
- Resources can access each other in the same namespace with their first name by the DNS name for other namespaces

Cluster
│
├── kube-system      → system components (kube-dns, coredns)
├── kube-public      → public resources
├── kube-node-lease  → node lease tracking
├── default          → default namespace
│
├── dev              → developers
├── staging          → QA/UAT
├── prod             → production workloads
│
└── monitoring       → Prometheus, Grafana, Loki, ELK
### List namespaces
``` bash
 kubectl get ns
```
### Create namespace
```bash
kubectl create namespace <name>
```
### delete namespace
```bash
kubectl delete namespace <name>
```
### to delpoy a file in aspecific namespace
```bash
kubectl apply -f deploy.yaml -n <namespace-name>
```
### Describe namespace
```bash
kubectl describe namespace <name>
```
### YAML Example
```bash
apiVersion: v1
kind: Namespace
metadata:
  name: dev
```
### Deploy a Pod in that namespace
```bash
apiVersion: v1
kind: Pod
metadata:
  name: nginx
  namespace: dev
spec:
  containers:
  - name: nginx
    image: nginx
```
