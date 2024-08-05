# Kubernetes Cheat Sheet

## Introduction to Kubernetes

Kubernetes, often referred to as K8s, is an open-source platform designed to automate deploying, scaling, and operating application containers. It allows you to manage containerized applications across multiple hosts and provides basic mechanisms for deployment, maintenance, and scaling of applications.

## Installation

### Install Minikube (Local Kubernetes)

1. **Download Minikube**: Follow the [Minikube Installation Guide](https://minikube.sigs.k8s.io/docs/start/) to download and install Minikube.
2. **Start Minikube**: Launch a local Kubernetes cluster with Minikube.

    ```bash
    minikube start
    ```

### Install kubectl (Kubernetes CLI)

1. **Download kubectl**: Refer to the [kubectl Installation Guide](https://kubernetes.io/docs/tasks/tools/install-kubectl/) for installation instructions.
2. **Verify Installation**: Ensure kubectl is installed correctly by checking its version.

    ```bash
    kubectl version --client
    ```

## Basic kubectl Commands

### Cluster Information

- **Check Cluster Info**: Display the endpoints and services in your cluster.

    ```bash
    kubectl cluster-info
    ```

- **View Nodes**: List all nodes in the cluster.

    ```bash
    kubectl get nodes
    ```

### Working with Pods

- **List Pods**: Display all pods in the current namespace.

    ```bash
    kubectl get pods
    ```

- **Describe Pod**: Get detailed information about a specific pod.

    ```bash
    kubectl describe pod <pod-name>
    ```

- **Delete Pod**: Remove a pod from the cluster.

    ```bash
    kubectl delete pod <pod-name>
    ```

### Deployments

- **Create Deployment**: Create a deployment with a specified image.

    ```bash
    kubectl create deployment <deployment-name> --image=<image-name>
    ```

- **List Deployments**: Display all deployments in the current namespace.

    ```bash
    kubectl get deployments
    ```

- **Scale Deployment**: Adjust the number of replicas for a deployment.

    ```bash
    kubectl scale deployment <deployment-name> --replicas=<number>
    ```

- **Update Deployment Image**: Update the image of a specific container in a deployment.

    ```bash
    kubectl set image deployment/<deployment-name> <container-name>=<new-image>
    ```

- **Delete Deployment**: Remove a deployment from the cluster.

    ```bash
    kubectl delete deployment <deployment-name>
    ```

### Services

- **Expose Pod as a Service**: Create a service to expose a pod to the outside world or within the cluster.

    ```bash
    kubectl expose pod <pod-name> --type=<service-type> --port=<port>
    ```

- **List Services**: Display all services in the current namespace.

    ```bash
    kubectl get services
    ```

### Namespaces

- **List Namespaces**: Display all namespaces in the cluster.

    ```bash
    kubectl get namespaces
    ```

- **Create Namespace**: Create a new namespace.

    ```bash
    kubectl create namespace <namespace-name>
    ```

- **Delete Namespace**: Remove a namespace from the cluster.

    ```bash
    kubectl delete namespace <namespace-name>
    ```

### ConfigMaps and Secrets

- **Create ConfigMap**: Store non-confidential data in a key-value pair format.

    ```bash
    kubectl create configmap <configmap-name> --from-literal=<key>=<value>
    ```

- **List ConfigMaps**: Display all ConfigMaps in the current namespace.

    ```bash
    kubectl get configmaps
    ```

- **Create Secret**: Store confidential data such as passwords and API keys.

    ```bash
    kubectl create secret generic <secret-name> --from-literal=<key>=<value>
    ```

- **List Secrets**: Display all secrets in the current namespace.

    ```bash
    kubectl get secrets
    ```

## Advanced Topics

### Persistent Volumes (PV) and Persistent Volume Claims (PVC)

- **Create PV**: Define a persistent storage resource.

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

- **Create PVC**: Request storage from a PersistentVolume.

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

- **Create Ingress**: Define rules to route external HTTP/S traffic to services within the cluster.

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

- **Install Helm**: Follow the [Helm Installation Guide](https://helm.sh/docs/intro/install/) to install Helm.
- **Add Helm Repo**: Add a new Helm chart repository.

    ```bash
    helm repo add <repo-name> <repo-url>
    ```

- **Install Helm Chart**: Deploy an application using a Helm chart.

    ```bash
    helm install <release-name> <chart-name>
    ```

- **List Helm Releases**: Display all Helm releases in the cluster.

    ```bash
    helm list
    ```

## Conclusion

This cheatsheet provides a quick reference to the most commonly used Kubernetes commands and concepts. With this guide, you'll be well-equipped to start deploying and managing your containerized applications using Kubernetes. 


## Author
**Purva Patel**
