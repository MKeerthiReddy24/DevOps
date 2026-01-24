### Different ways of creating a Kubernetes object
Imperative way ( Through command or API calls)
Declarative way ( By creating manifest files)
<img width="903" height="406" alt="image" src="https://github.com/user-attachments/assets/e7aff5fb-0439-42dc-8e95-8074932797f9" />

#### Imperative way we can create a pod using below command
```bash
kubectl run <pod-name> --image=nginx:latest
```
#### Declarative way of creating a pod is to by using a manifest file like below which is written yaml or json.
```bash
# This is a sample pod yaml file

apiversion: v1
kind: Pod
metadata:
  name: nginx-pod
  labels:
    env:demo
    type:frontend
spec:
  containers:
  - name: nginx-container
    image: nginx
    ports:
     - containerPort: 80
```

#### Create the YAML from the nginx pod existed created
```bash
kubectl get pod <pod-name> -o yaml > pod.yaml
```
##### To get the clean manifest file without any runtime information
```bash
kubectl run <pod-name> --image=nginx --dry-run=client -o yaml > <new-file-name.yaml>
```
##### In Kubernetes, dry run means:
“Show me what would happen, but don’t actually create anything.”
It validates the command and prints the output without applying it to the cluster.

#### Use that YAML to create a new pod with the name nginx-new.
Modify the pod name under metadata and then run below command
```bash
kubectl apply -f <file.yaml>
```

#### To describe the pod
```bash
kubectl describe <pod-name>
```

#### To view the pods
```bash
kubectl get pods
```



