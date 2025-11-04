<img width="860" height="800" alt="architecture excalidraw (1)" src="https://github.com/user-attachments/assets/4f298588-b5a5-45d4-b34a-482a788fbcda" />

**Example Voting App – Azure DevOps Deployment**

This project demonstrates the deployment of a **microservices-based voting application** using **Docker**, **Kubernetes (AKS)**, and **Azure DevOps CI/CD pipelines**.  
It is based on the open-source [Example Voting App](https://github.com/dockersamples/example-voting-app) and customized for deployment on **Microsoft Azure Cloud**.

---

**Architecture Overview**

The application is built with five containerized services:
| Service | Technology | Description |
|----------|-------------|-------------|
| **Vote** | Python (Flask) | Frontend for users to cast votes |
| **Result** | Node.js | Frontend for displaying results |
| **Worker** | .NET / Java | Backend processor handling vote queue |
| **Redis** | In-memory cache | Stores temporary votes |
| **PostgreSQL** | Database | Persists final voting results |

---

**Tools & Technologies Used**

**Azure** • **Azure Kubernetes Service (AKS)** • **Azure Container Registry (ACR)** • **Terraform** • **Azure DevOps CI/CD**  
**Docker** • **Kubernetes** • **Prometheus** • **Grafana** • **Python** • **Linux**

---

**Deployment Workflow**

**Step 1: Build & Run Locally**
Built and tested all microservices locally using Docker Compose:
```bash
docker-compose build
docker-compose up -d


**Step 2: Push Images to Azure Container Registry (ACR)**
az acr build --registry tanyaregistry --image votingapp/vote:v1 .
az acr build --registry tanyaregistry --image votingapp/result:v1 .


**Step 3: Provision AKS Cluster with Terraform**
terraform init
terraform plan
terraform apply

**Step 4: Deploy to Kubernetes**
kubectl apply -f k8s-manifests/


**Step 5: Set Up CI/CD with Azure DevOps**
Configured Azure Pipelines (YAML) for automated build and deploy on commit.
Connected GitHub repo → Azure DevOps → AKS cluster.
Used environment variables and secrets securely from Azure Key Vault.

**Step 6: Monitoring & Visualization**
Installed Prometheus and Grafana on AKS for cluster monitoring.
Created dashboards to visualize resource usage, pods health, and traffic.

**See the /screenshots folder for more visuals of the deployment and monitoring setup.**

**Original Source: dockersamples/example-voting-app**
Customized and deployed  Azure Kubernetes Service (AKS) using CI/CD automation.


