### **Step-by-Step: Port Forwarding in Minikube**  

#### **Step 1: Start Minikube**
If Minikube is not already running, start it:  
```bash
minikube start
```

#### **Step 2: Verify Kubernetes Resources**
Check if the service is running:  
```bash
kubectl get all
```
If the service is missing, reapply the configuration:  
```bash
kubectl apply -f service.yaml
```

#### **Step 3: Ensure No Conflicting Processes**
Kill any running Minikube processes:  
```bash
pkill -9 -f "minikube"
```
Check for any active `kubectl` processes:  
```bash
ps aux | grep kubectl
```
Terminate any lingering `kubectl` processes:  
```bash
pkill -9 -f "kubectl"
```
Verify Kubernetes resources are still available:  
```bash
kubectl get all
```

#### **Step 4: Start Port Forwarding**
Forward local port 8080 to the Kubernetes service:  
```bash
kubectl port-forward svc/myapp-service 8080:80
```
Leave this command running.

#### **Step 5: Access the Service**
Open a new terminal and test it:  
```bash
curl http://localhost:8080
```
If successful, this returns the Nginx welcome page.

#### **Step 6: Stop Port Forwarding**
If needed, stop port forwarding by pressing `CTRL + C` in the terminal where it’s running.  

If running in the background, find the process ID:  
```bash
ps aux | grep kubectl
```
Kill it:  
```bash
pkill -9 -f "kubectl"
```

This ensures a clean state for future port forwarding.