# Kubernetes Commands

- Create a replicaset:
  ```sh
  kubectl create -f replicaset-definition.k8s.yaml
  ```

- Get replicaset:
  ```sh
  kubectl get replicaset
  ```

- Delete a replicaset:
  ```sh
  kubectl delete replicaset myapp-replicaset
  ```

- Replace a replicaset:
  ```sh
  kubectl replace -f replicaset-definition.k8s.yaml
  ```

- Scale a replicaset:
  ```sh
  kubectl scale --replicas=6 -f replicaset-definition.k8s.yaml
  ```

- Get pods:
  ```sh
  kubectl get pods
  ```
