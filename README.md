# 🚀 ISEC6000-SecureDevOps

  
## 🌟 Project Description

ISEC6000-SecureDevOps is a project for deploying and securing a microservices-based e-commerce application named **Saleor**. This project involves setting up infrastructure with ** Kubernetes ** deploying Saleor local enviornment using **Docker** and **Kubernetes-Kind**, and implementing various security measures to ensure a robust deployment. 
  
### 🔑 Key Features:

- **Infrastructure Setup**: Create and configure a Kubernetes cluster on Kind.
- **Deployment**: Deploy Saleor using Docker Compose and Kubernetes.
- **Security**: Implement container security measures and perform vulnerability scanning.
- **Version Control**: Use GitHub for source code management and version control.
- **Local Development**: Utilize `kind` for local Kubernetes development.
## 📑 Table of Contents
1. [Cloning the Project](#cloning-the-project)
2. [Installation and Setup](#installation-and-setup)
2.1. [Create a Kubernetes Cluster](#create-a-kubernetes-cluster)
2.2. [Configure kubectl](#configure-kubectl)
2.3.  [GitHub Repository Setup](#github-repository-setup)
2.4 [Explore Saleor](#explore-saleor)
2.5 [Customize and Deploy](#customize-and-deploy)
2.6[Kubernetes Local Deployment with kind](#kubernetes-local-deployment-with-kind)
2.7[Implement Security Measures](#implement-security-measures)
3. [Credits](#credits)

## 🔧 1. Cloning the Project
 Cloning the Project To clone the project repository, run the following command: 
 **```git clone https://github.com/SanjanaJayaramM93/ISEC6000-SecureDevOps.git cd ISEC6000-SecureDevOps```**

## 🔧 2. Installation and Setup
 ### 🛠️2.1. Create a kind Cluster
   i.  **Install Kind**
   * Kind installation page : [kind](https://kind.sigs.k8s.io/docs/user/quick-start)
   * On Linux:
```bash
# For AMD64 / x86_64
[ $(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.24.0/kind-linux-amd64
# For ARM64
[ $(uname -m) = aarch64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.24.0/kind-linux-arm64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind![Copy](https://kind.sigs.k8s.io/copycode.svg)
```
   ii.   **Create a Kind Cluster**
   ```kind create cluster --name cluster-name```
   iii. **Verify Cluster**
   ```kind get cluster```
   ### 🛠️2.2 **Configure kubectl kubectl**
   i.  **Install kubectl**
   * Kubectl Installation:[Link](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/)
   * ``curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"``
     
   ii.  **Verify Installation**
     *  ``` _kubectl version --client```
     iv **Verify Connection**
```kubectl cluster-info```
  ### 🛠️2.3 **Convert Docker Files Compose YAML files**
   i.**Install Kompose**
   *Kompose installation: [Link](https://github.com/kubernetes/kompose)
    **Linux:**
```curl -L https://github.com/kubernetes/kompose/releases/download/v1.34.0/kompose-linux-amd64 -o kompose```
* Verify version.
```Kompose version```

ii.**Convert Docker Compose YAML files to Kubernetes YAML files using Kompose**
   ```Kompose convert```
   
   iii.**Follow the deployment guidelines in the [Saleor platform](https://github.com/saleor/saleor-platform) repository to deploy the Saleor stack on Kubernetes.**
     
   iv.**Apply Django migrations**
   ```docker compose run --rm api python3 manage.py migrate.```
   v.**Populate the database with example data and create the admin user.**
   ```docker compose run --rm api python3 manage.py populatedb – createsuperuser```
   ### 🛠️2.5 **Kubernetes Local Deployment with kind**
   i· **Verify Deployment**
   a. List all the pods running in the cluster.
     ```kubectl, get pods```
   b. Displays all the services running in the cluster, which route traffic to the pods
   ```kubectl get service```
  c.  Informationn about deployment
  ```kubectl get deployments```
   d. information about a specific node
   ```kubectl get nodes```
   ### 🛠️2.6 **Access services**
   *To access services :
```kubectl port-forward TYPE/NAME [options] [LOCAL_PORT:]REMOTE_PORT```
  -   Saleor Core (API) - [http://localhost:8000](http://localhost:8000/)
-   Saleor Dashboard - [http://localhost:9000](http://localhost:9000/)
-   Jaeger UI (APM) - [http://localhost:16686](http://localhost:16686/)
-  Mailpit (Test email interface) - [http://localhost:8025](http://localhost:8025/)
   
 ### 🛠️2.7**Implement Security Measures**
   Install Trivy for vulnerability scanning.:[Link](https://github.com/aquasecurity/trivy).
   #### General usage
    ```trivy <target> [--scanners <scanner1,scanner2>] <subject>```
    
   Sample: 
    ```trivy image python:3.4-alpine```

## 🔧 4. Credits

-   **Saleor**: An open-source e-commerce platform that serves as the core of this project. [Saleor GitHub Repository](https://github.com/saleor/saleor)
-   **Kind**: A tool for running local Kubernetes clusters using Docker container nodes. [Kind GitHub Repository](https://github.com/kubernetes-sigs/kind)
-   **Kompose**: A tool to convert Docker Compose files to Kubernetes resource files. [Kompose GitHub Repository](https://github.com/kubernetes/kompose)
-   **Trivy**: A vulnerability scanner for containers and other artifacts. [Trivy GitHub Repository](https://github.com/aquasecurity/trivy)


 


  
  
  
  
  

  

