## Kubernetes
Kubernetes, often abbreviated as K8s, is an open-source container orchestration platform designed to automate the deployment, scaling, and management of containerized applications.
It was originally developed by Google and is now maintained by the Cloud Native Computing Foundation (CNCF)

## Core Concepts of Kubernetes

**Pod:** The smallest deployable unit in Kubernetes, representing one or more containers running together with shared resources.

**Node:** A machine (physical or virtual) that runs pods. Nodes are managed by a central control plane.

**Cluster:** A set of nodes that work together to run containerized applications.

**Deployment:** A higher-level abstraction for managing the lifecycle of pods, ensuring the desired number of replicas are running.

**Service:** A stable network endpoint to expose pods, enabling communication between different components of the application.

**ConfigMap & Secret:** Tools to manage configuration data and sensitive information like passwords and API keys.

## Kubernetes Architecture
![image](https://github.com/user-attachments/assets/91ae313f-562f-4537-bb28-0b62e91e4c9f)

## Master Node

**API Server:** The main entry point to the cluster for managing resources via RESTful API calls.

**Scheduler:** Assigns workloads to nodes based on resource availability and policies.

**Controller Manager:** Ensures the desired state of the cluster (e.g., maintaining replicas).

**etcd:** A distributed key-value store for storing cluster state and configuration.

## Worker Node

**Kubelet:** An agent that ensures containers are running in a pod on a node.

**Kube-proxy:** Handles networking and load balancing for services.

**Container Runtime:** Software responsible for running containers (e.g., Docker, containers).


## Use Case of Kubernetes

**Microservices:** Deploying and managing loosely coupled services.


**CI/CD Pipelines:** Automating application build, testing, and deployment.

**Hybrid Cloud Deployments:** Managing workloads across on-premises and cloud environments.

**Big Data and AI/ML:** Running data pipelines and training machine learning models.

## Getting Started with Kubernetes

**Minikube:** A lightweight tool for running Kubernetes locally.

**kubectl:** A CLI tool to interact with a Kubernetes cluster.

**Kubeadm:** Provide Multiple node cluster

**Cloud Providers:** Managed Kubernetes services like Google Kubernetes Engine (GKE), Amazon Elastic Kubernetes Service (EKS), and Azure Kubernetes Service (AKS).

