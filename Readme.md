# 🚀 2048 Game Deployment on AWS EKS using Fargate

A cloud-native deployment project where the popular **2048 Game Application** was deployed on an **Amazon EKS Cluster with AWS Fargate**. This project demonstrates Kubernetes deployment, AWS ALB Ingress integration, IAM configuration, and serverless container execution using **kubectl**, **eksctl**, and **AWS CLI**.

---

# 📌 Project Overview

This project focuses on deploying a static web-based 2048 game application on a fully managed Kubernetes environment using **Amazon Elastic Kubernetes Service (EKS)** with **AWS Fargate**.

Instead of managing EC2 worker nodes manually, the application runs serverlessly using **Fargate Profiles**, reducing infrastructure management overhead.

The application is exposed publicly using:

- AWS Load Balancer Controller
- Application Load Balancer (ALB)
- Kubernetes Ingress

---

# 🛠️ Technologies Used

- AWS EKS
- AWS Fargate
- Kubernetes
- AWS Load Balancer Controller
- Application Load Balancer (ALB)
- IAM Roles & Policies
- kubectl
- eksctl
- AWS CLI
- Docker

---

# 🏗️ Architecture

```text
User → ALB Ingress → Kubernetes Service → Deployment Pods → 2048 Game App
```

---

# 📂 Project Structure

```bash
.
├── deployment.yaml
├── ingress.yaml
├── namespace.yaml
├── service.yaml
└── README.md
```

---

# 📄 Kubernetes Manifest Files

## 1️⃣ namespace.yaml

Creates a dedicated Kubernetes namespace for organizing resources.

### Purpose
- Logical isolation of resources
- Better resource management

---

## 2️⃣ deployment.yaml

Defines the application deployment and manages the game pods.

### Includes
- Container image
- Replica configuration
- Port exposure
- Labels & selectors

---

## 3️⃣ service.yaml

Creates a Kubernetes Service to expose the deployment internally.

### Purpose
- Stable networking endpoint
- Pod communication handling

---

## 4️⃣ ingress.yaml

Configures ALB Ingress for external access.

### Features
- Internet-facing ALB
- Path-based routing
- Integration with AWS Load Balancer Controller

---

# ⚙️ AWS Services & Configurations

## ✅ Amazon EKS

Managed Kubernetes control plane used to orchestrate containers.

---

## ✅ AWS Fargate

Used for serverless execution of Kubernetes pods without managing EC2 worker nodes.

### Benefits
- No server management
- Auto scaling
- Better resource isolation

---

## ✅ AWS Load Balancer Controller

Installed in the EKS cluster to automatically provision and manage AWS Application Load Balancers.

---

## ✅ IAM Roles & Policies

Custom IAM Roles and Policies were configured to allow:

- Kubernetes pods to communicate with AWS services
- ALB Controller to create/manage ALBs
- Proper EKS authentication and authorization

---

# 🚀 Deployment Workflow

## Step 1 — Create EKS Cluster

```bash
eksctl create cluster \
--name 2048-cluster \
--region <region-name> \
--fargate
```

---

## Step 2 — Configure kubectl

```bash
aws eks update-kubeconfig \
--region <region-name> \
--name 2048-cluster
```

---

## Step 3 — Create Namespace

```bash
kubectl apply -f namespace.yaml
```

---

## Step 4 — Deploy Application

```bash
kubectl apply -f deployment.yaml
```

---

## Step 5 — Create Service

```bash
kubectl apply -f service.yaml
```

---

## Step 6 — Configure Ingress

```bash
kubectl apply -f ingress.yaml
```

---

## Step 7 — Verify Resources

```bash
kubectl get all -n <namespace>
```

```bash
kubectl get ingress -n <namespace>
```

---

# 🌐 Application Access

After successful deployment:

1. AWS ALB gets automatically provisioned
2. ALB DNS URL becomes available
3. Open the ALB DNS in browser
4. Access the 2048 Game Application

---

# 📸 Project Screenshot

## 2048 Game Application
<img width="1327" height="875" alt="WhatsApp Image 2026-05-18 at 03 21 55" src="https://github.com/user-attachments/assets/cece5497-f1f8-4ae2-a014-e80d8ea256ae" />


---

# 🔐 Security & IAM

This project also involved configuring IAM permissions required for:

- AWS Load Balancer Controller
- EKS Service Account access
- Pod communication with AWS services

IAM Roles and Policies were carefully attached to ensure secure interaction between Kubernetes workloads and AWS infrastructure.

---

# 🎯 Key Learnings

- Kubernetes resource management
- EKS cluster creation and management
- Serverless Kubernetes using Fargate
- ALB Ingress integration
- IAM Roles for Service Accounts (IRSA)
- Kubernetes networking concepts
- AWS cloud-native deployment workflow

---

# 📈 Future Improvements

- Add CI/CD using GitHub Actions
- Infrastructure provisioning using Terraform
- Monitoring using Prometheus & Grafana
- HTTPS using ACM certificates
- Auto scaling configurations

---

# 👨‍💻 Author

## Dhruv Goel

AWS | Cloud | DevOps Enthusiast

---
