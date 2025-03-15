### **Kubernetes Commands**

#### **Basic Cluster Operations**
- **Check cluster info:**
  ```sh
  kubectl cluster-info
  ```
- **View cluster nodes:**
  ```sh
  kubectl get nodes
  ```
- **Get detailed node information:**
  ```sh
  kubectl describe node <node-name>
  ```
- **Check Kubernetes API resources:**
  ```sh
  kubectl api-resources
  ```
- **Check Kubernetes API versions:**
  ```sh
  kubectl api-versions
  ```
- **View Kubernetes configuration context:**
  ```sh
  kubectl config view
  ```

---

#### **Pod Management**
- **Create a pod from a YAML file:**
  ```sh
  kubectl apply -f pod-definition.yaml
  ```
- **List all pods in the cluster:**
  ```sh
  kubectl get pods
  ```
- **List pods with detailed output:**
  ```sh
  kubectl get pods -o wide
  ```
- **Describe a specific pod:**
  ```sh
  kubectl describe pod <pod-name>
  ```
- **Delete a specific pod:**
  ```sh
  kubectl delete pod <pod-name>
  ```
- **Delete all pods in a namespace:**
  ```sh
  kubectl delete pods --all -n <namespace>
  ```
- **Force delete a pod (if stuck terminating):**
  ```sh
  kubectl delete pod <pod-name> --grace-period=0 --force
  ```
- **Run a temporary pod interactively:**
  ```sh
  kubectl run my-temp-pod --image=nginx --restart=Never -it -- sh
  ```
- **Restart a pod (by deleting it, since Kubernetes will recreate it):**
  ```sh
  kubectl delete pod <pod-name>
  ```

---

#### **ReplicaSet Management**
- **Create a ReplicaSet:**
  ```sh
  kubectl create -f replicaset-definition.yaml
  ```
- **Get all ReplicaSets:**
  ```sh
  kubectl get replicaset
  ```
- **Delete a specific ReplicaSet:**
  ```sh
  kubectl delete replicaset <replicaset-name>
  ```
- **Scale a ReplicaSet:**
  ```sh
  kubectl scale --replicas=6 -f replicaset-definition.yaml
  ```
- **Manually edit a ReplicaSet:**
  ```sh
  kubectl edit replicaset <replicaset-name>
  ```

---

#### **Deployment Management**
- **Create a Deployment:**
  ```sh
  kubectl create deployment myapp --image=nginx
  ```
- **Get all Deployments:**
  ```sh
  kubectl get deployments
  ```
- **Describe a Deployment:**
  ```sh
  kubectl describe deployment <deployment-name>
  ```
- **Scale a Deployment:**
  ```sh
  kubectl scale deployment <deployment-name> --replicas=5
  ```
- **Update a Deployment’s image:**
  ```sh
  kubectl set image deployment/myapp nginx=nginx:1.19
  ```
- **Pause a Deployment (prevent changes from rolling out):**
  ```sh
  kubectl rollout pause deployment myapp
  ```
- **Resume a Deployment rollout:**
  ```sh
  kubectl rollout resume deployment myapp
  ```
- **Rollback a Deployment:**
  ```sh
  kubectl rollout undo deployment myapp
  ```
- **Restart a Deployment:**
  ```sh
  kubectl rollout restart deployment myapp
  ```

---

#### **Service & Networking**
- **Get all Services:**
  ```sh
  kubectl get services
  ```
- **Expose a Deployment as a Service:**
  ```sh
  kubectl expose deployment myapp --type=LoadBalancer --port=80
  ```
- **Port-forward a service to localhost:**
  ```sh
  kubectl port-forward svc/<service-name> 8080:80
  ```
- **Port-forward a pod to localhost:**
  ```sh
  kubectl port-forward pod/<pod-name> 8080:80
  ```
- **Get information about a specific service:**
  ```sh
  kubectl describe service <service-name>
  ```
- **Delete a Service:**
  ```sh
  kubectl delete service <service-name>
  ```
- **List all endpoints (see where services are routing traffic):**
  ```sh
  kubectl get endpoints
  ```

---

#### **Namespace Management**
- **List all namespaces:**
  ```sh
  kubectl get namespaces
  ```
- **Create a new namespace:**
  ```sh
  kubectl create namespace my-namespace
  ```
- **Delete a namespace:**
  ```sh
  kubectl delete namespace my-namespace
  ```
- **Run commands inside a namespace:**
  ```sh
  kubectl get pods -n <namespace>
  kubectl apply -f my-config.yaml -n <namespace>
  ```

---

#### **Logs & Debugging**
- **View logs for a pod:**
  ```sh
  kubectl logs <pod-name>
  ```
- **Stream live logs for a pod:**
  ```sh
  kubectl logs -f <pod-name>
  ```
- **View logs from a specific container inside a pod:**
  ```sh
  kubectl logs <pod-name> -c <container-name>
  ```
- **Run a command inside a running pod:**
  ```sh
  kubectl exec -it <pod-name> -- /bin/sh
  ```
- **Check for issues in pods:**
  ```sh
  kubectl get events
  ```
- **Debug a failing pod by running a debug container:**
  ```sh
  kubectl debug <pod-name> -it --image=busybox -- /bin/sh
  ```

---

#### **ConfigMap & Secret Management**
- **Create a ConfigMap from a file:**
  ```sh
  kubectl create configmap my-config --from-file=config-file.conf
  ```
- **View all ConfigMaps:**
  ```sh
  kubectl get configmaps
  ```
- **Describe a ConfigMap:**
  ```sh
  kubectl describe configmap my-config
  ```
- **Delete a ConfigMap:**
  ```sh
  kubectl delete configmap my-config
  ```
- **Create a Secret:**
  ```sh
  kubectl create secret generic my-secret --from-literal=password=mysecurepassword
  ```
- **View all Secrets:**
  ```sh
  kubectl get secrets
  ```
- **Describe a Secret (will not show decoded values):**
  ```sh
  kubectl describe secret my-secret
  ```

---

#### **Persistent Volume & Storage**
- **Get all PersistentVolumes (PVs):**
  ```sh
  kubectl get pv
  ```
- **Get all PersistentVolumeClaims (PVCs):**
  ```sh
  kubectl get pvc
  ```
- **Describe a PersistentVolumeClaim:**
  ```sh
  kubectl describe pvc my-pvc
  ```
- **Delete a PersistentVolumeClaim:**
  ```sh
  kubectl delete pvc my-pvc
  ```

---

#### **Resource Usage & Monitoring**
- **Check CPU & memory usage of pods:**
  ```sh
  kubectl top pod
  ```
- **Check CPU & memory usage of nodes:**
  ```sh
  kubectl top node
  ```
- **Watch resource usage live:**
  ```sh
  kubectl top pod --watch
  ```
- **View metrics for a specific pod:**
  ```sh
  kubectl top pod <pod-name>
  ```

---

#### **Apply vs. Create**
- **Apply a configuration (best for updates & idempotency):**
  ```sh
  kubectl apply -f config.yaml
  ```
- **Create a resource (fails if it already exists):**
  ```sh
  kubectl create -f config.yaml
  ```

---

#### **Miscellaneous**
- **Delete all resources in a namespace:**
  ```sh
  kubectl delete all --all -n <namespace>
  ```
- **Restart all pods in a namespace:**
  ```sh
  kubectl delete pods --all -n <namespace>
  ```
- **Dry-run a command (test without execution):**
  ```sh
  kubectl apply -f deployment.yaml --dry-run=client
  ```
- **View all API resources available:**
  ```sh
  kubectl api-resources
  ```
- **View all available API versions:**
  ```sh
  kubectl api-versions
  ```

---
