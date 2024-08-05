# Kubernetes Cheat Sheet

## Introduction to Kubernetes

Kubernetes, often referred to as K8s, is an open-source platform designed to automate deploying, scaling, and operating application containers. It allows you to manage containerized applications across multiple hosts and provides basic mechanisms for deployment, maintenance, and scaling of applications.


## Installation

### Install Minikube (Local Kubernetes)
1. **Download Minikube**: [Minikube Installation Guide](https://minikube.sigs.k8s.io/docs/start/)
2. **Start Minikube**:
   
    ```bash
    minikube start
    ```

### Install kubectl (Kubernetes CLI)
1. **Download kubectl**: [kubectl Installation Guide](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
2. **Verify Installation**:
   
    ```bash
    kubectl version --client
    ```


## Basic kubectl Commands

### Cluster Information
- **Check Cluster Info**:

    ```bash
    kubectl cluster-info
    ```
- **View Nodes**:
  
    ```bash
    kubectl get nodes
    ```

### Working with Pods
- **List Pods**:
  
    ```bash
    kubectl get pods
    ```
- **Describe Pod**:
  
    ```bash
    kubectl describe pod <pod-name>
    ```
- **Delete Pod**:
  
    ```bash
    kubectl delete pod <pod-name>
    ```

### Deployments
- **Create Deployment**:
  
    ```bash
    kubectl create deployment <deployment-name> --image=<image-name>
    ```
- **List Deployments**:
  
    ```bash
    kubectl get deployments
    ```
- **Scale Deployment**:
  
    ```bash
    kubectl scale deployment <deployment-name> --replicas=<number>
    ```
- **Update Deployment Image**:
  
    ```bash
    kubectl set image deployment/<deployment-name> <container-name>=<new-image>
    ```
- **Delete Deployment**:
  
    ```bash
    kubectl delete deployment <deployment-name>
    ```

### Services
- **Expose Pod as a Service**:
  
    ```bash
    kubectl expose pod <pod-name> --type=<service-type> --port=<port>
    ```
- **List Services**:
  
    ```bash
    kubectl get services
    ```

### Namespaces
- **List Namespaces**:
  
    ```bash
    kubectl get namespaces
    ```
- **Create Namespace**:
  
    ```bash
    kubectl create namespace <namespace-name>
    ```
- **Delete Namespace**:
  
    ```bash
    kubectl delete namespace <namespace-name>
    ```

### ConfigMaps and Secrets
- **Create ConfigMap**:
  
    ```bash
    kubectl create configmap <configmap-name> --from-literal=<key>=<value>
    ```
- **List ConfigMaps**:
  
    ```bash
    kubectl get configmaps
    ```
- **Create Secret**:
  
    ```bash
    kubectl create secret generic <secret-name> --from-literal=<key>=<value>
    ```
- **List Secrets**:
  
    ```bash
    kubectl get secrets
    ```



## Advanced Topics

### Persistent Volumes (PV) and Persistent Volume Claims (PVC)
- **Create PV**:
  
    ```yaml
    apiVersion: v1
    kind: PersistentVolume
    metadata:
      name: <pv-name>
    spec:
      capacity:
        storage: <storage-size>
      accessModes:
        - ReadWriteOnce
      hostPath:
        path: "<host-path>"
    ```
- **Create PVC**:
  
    ```yaml
    apiVersion: v1
    kind: PersistentVolumeClaim
    metadata:
      name: <pvc-name>
    spec:
      accessModes:
        - ReadWriteOnce
      resources:
        requests:
          storage: <storage-size>
    ```

### Ingress
- **Create Ingress**:
  
    ```yaml
    apiVersion: networking.k8s.io/v1
    kind: Ingress
    metadata:
      name: <ingress-name>
    spec:
      rules:
      - host: <host>
        http:
          paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: <service-name>
                port:
                  number: <service-port>
    ```

### Helm
- **Install Helm**: [Helm Installation Guide](https://helm.sh/docs/intro/install/)
- **Add Helm Repo**:
  
    ```bash
    helm repo add <repo-name> <repo-url>
    ```
- **Install Helm Chart**:
  
    ```bash
    helm install <release-name> <chart-name>
    ```
- **List Helm Releases**:
  
    ```bash
    helm list
    ```



## Conclusion

This cheatsheet provides a quick reference to the most commonly used Kubernetes commands and concepts. With this guide, you'll be well-equipped to start deploying and managing your containerized applications using Kubernetes. For more detailed information, refer to the [Kubernetes Documentation](https://kubernetes.io/docs/).

## Author
**Purva Patel**
