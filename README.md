# 🚀 Cloud-Native DevOps Project

<p align="center">
  <img src="https://imgur.com/cp6cwlX.png" alt="Cloud-Native DevOps Project Banner" width="100%">
</p>

<p align="center">
  <strong>Automate • Deploy • Scale • Secure</strong>
</p>

<p align="center">
  A production-oriented cloud-native infrastructure project demonstrating modern DevOps practices, AWS cloud services, Kubernetes orchestration, Infrastructure as Code, and automated CI/CD workflows.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/AWS-Cloud-orange?logo=amazonaws">
  <img src="https://img.shields.io/badge/Terraform-IaC-purple?logo=terraform">
  <img src="https://img.shields.io/badge/Jenkins-CI%2FCD-red?logo=jenkins">
  <img src="https://img.shields.io/badge/Docker-Containers-blue?logo=docker">
  <img src="https://img.shields.io/badge/Kubernetes-EKS-blue?logo=kubernetes">
  <img src="https://img.shields.io/badge/DevOps-Automation-success">
</p>

---

## 📋 Project Overview

This repository demonstrates a comprehensive cloud-native application deployment using modern DevOps tools and AWS cloud infrastructure.

The project focuses on automating the complete software delivery lifecycle through Infrastructure as Code, containerization, orchestration, continuous integration, continuous deployment, security scanning, and monitoring.

### Key Objectives

- Infrastructure automation using Terraform
- Container orchestration with Amazon EKS
- CI/CD pipeline implementation using Jenkins
- Artifact management using Nexus
- Code quality analysis with SonarQube
- Security scanning using CodeQL and Veracode
- Cloud infrastructure monitoring and observability
- Scalable and secure application deployment

## 🏗️ Infrastructure as Code — Terraform

The infrastructure is provisioned using Terraform, enabling automated, repeatable, and version-controlled cloud resource management.

Terraform state management and locking are configured using AWS S3 and appropriate state-locking mechanisms.

### AWS Resources

**Networking**
- Amazon VPC
- Public, private, and database subnets
- Internet Gateway
- NAT Gateway
- Route Tables
- Security Groups

**Compute & Kubernetes**
- Amazon EKS
- EC2 Bastion Host
- Jenkins Server
- Jenkins Agent

**Storage & Database**
- Amazon RDS MySQL
- Amazon EFS
- Amazon S3
- Amazon ECR

**Networking & Security**
- Amazon Route 53
- AWS Application Load Balancer
- AWS CloudFront
- AWS Certificate Manager
- AWS KMS

### Terraform Directory Structure

```text
terraform/
├── 00-vpc/
├── 10-sg/
├── 20-bastion/
├── 30-db/
├── 40-eks/
├── 50-acm/
├── 60-ingress-alb/
└── 70-ecr/
```

> Refer to the Terraform directory for infrastructure provisioning instructions.

## ☸️ Kubernetes Architecture — Amazon EKS

The application is deployed on Amazon Elastic Kubernetes Service (EKS), providing container orchestration, scalability, and availability.

### Cluster Configuration

- Amazon EKS managed Kubernetes
- Multi-AZ architecture
- On-demand and Spot worker nodes
- Horizontal Pod Autoscaling
- Rolling updates
- Health checks and readiness probes
- Resource requests and limits

### Kubernetes Components

**Traffic Management**
- AWS Application Load Balancer
- AWS Load Balancer Controller
- Kubernetes Ingress
- URL-based routing
- SSL/TLS termination

**Application Management**
- Kubernetes Deployments
- Services
- ConfigMaps
- Secrets
- Helm Charts
- Horizontal Pod Autoscaler

**Persistent Storage**
- Amazon EFS
- Persistent Volumes
- Persistent Volume Claims
- Dynamic storage provisioning

### Helm Chart Structure

```text
helm/
├── Chart.yaml
├── values.yaml
└── templates/
    ├── deployment.yaml
    ├── service.yaml
    ├── ingress.yaml
    ├── configmap.yaml
    ├── secret.yaml
    └── hpa.yaml
```

## 🚀 CI/CD Pipeline — Jenkins

The CI/CD pipeline automates application build, testing, code analysis, containerization, and deployment.

Jenkins integrates with GitHub through webhooks to trigger automated pipeline execution.

### Pipeline Workflow

```text
Developer
   │
   ▼
GitHub Repository
   │
   ▼
GitHub Webhook
   │
   ▼
Jenkins CI/CD Pipeline
   │
   ├── Code Checkout
   ├── Dependency Installation
   ├── Unit Testing
   ├── SonarQube Analysis
   ├── CodeQL Security Analysis
   ├── Docker Image Build
   ├── Container Security Scan
   ├── Artifact Upload to Nexus
   ├── Image Push to Amazon ECR
   ├── Terraform Infrastructure Management
   └── Kubernetes Deployment
           │
           ▼
       Amazon EKS
           │
           ▼
    Application Load Balancer
           │
           ▼
    Cloud-Native Application
```

### Pipeline Features

- Automated source code checkout
- Multi-stage Jenkins pipeline
- Parallel execution where appropriate
- Code quality verification
- Automated container builds
- Artifact management
- Infrastructure deployment
- Kubernetes rolling updates
- Deployment validation
- Failure notifications

### Jenkinsfile Structure

```groovy
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out source code'
            }
        }

        stage('Build') {
            steps {
                echo 'Building application'
            }
        }

        stage('Test') {
            steps {
                echo 'Running automated tests'
            }
        }

        stage('Docker Build') {
            steps {
                echo 'Building Docker image'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application'
            }
        }
    }
}
```

> This is an illustrative Jenkins pipeline. Replace placeholder stages with actual build, test, and deployment commands.

## 🛠️ Setup Instructions

### Prerequisites

- AWS Account
- GitHub Repository
- Docker
- Jenkins
- Terraform
- kubectl
- Helm
- AWS CLI
- Linux environment
- Domain name (optional)

### 1. Jenkins Setup

1. Launch an EC2 instance for Jenkins.
2. Configure the required security groups.
3. Install Java and Jenkins.
4. Start the Jenkins service.
5. Access the Jenkins dashboard.
6. Install the required plugins.

Example:

```bash
sudo systemctl enable jenkins
sudo systemctl start jenkins
sudo systemctl status jenkins
```

### 2. Jenkins Agent Setup

Configure a Jenkins agent with the required DevOps tools.

Install:

- Docker
- AWS CLI
- Terraform
- kubectl
- Helm
- Git

Configure the Jenkins controller-agent connection securely.

### 3. Nexus Repository Setup

Configure Nexus Repository Manager for artifact management.

- Create hosted Maven repositories.
- Configure Docker repositories if needed.
- Integrate Nexus with Jenkins.
- Configure credentials securely.
- Upload and retrieve build artifacts.

### 4. SonarQube Setup

Deploy SonarQube and integrate it with Jenkins.

Configure:

- SonarQube Server
- SonarQube Scanner
- Authentication Token
- Quality Gates
- Code Coverage
- Security Analysis

### 5. Terraform Infrastructure Setup

```bash
cd terraform

terraform init

terraform validate

terraform plan
```

Review infrastructure changes before applying:

```bash
terraform apply
```

### 6. Kubernetes Deployment

Configure AWS EKS access:

```bash
aws eks update-kubeconfig \
  --region YOUR_AWS_REGION \
  --name YOUR_EKS_CLUSTER
```

Deploy Kubernetes resources:

```bash
kubectl apply -f kubernetes/
```

Verify deployment:

```bash
kubectl get nodes

kubectl get pods

kubectl get services

kubectl get deployments
```

## 📊 Monitoring & Observability

### Monitoring Stack

| Tool | Purpose |
|---|---|
| Prometheus | Metrics collection |
| Grafana | Monitoring dashboards |
| AWS CloudWatch | AWS monitoring |
| ELK Stack | Centralized logging |
| PagerDuty | Incident notifications |

### Monitoring Capabilities

- Application performance monitoring
- Kubernetes cluster monitoring
- CPU and memory utilization
- Infrastructure metrics
- Application logs
- Alerting and notifications
- Deployment health monitoring

## 🔐 Security & DevSecOps

Security is integrated throughout the application development and deployment lifecycle.

### Security Tools

| Tool | Purpose |
|---|---|
| SonarQube | Code quality and security analysis |
| CodeQL | Code security analysis |
| Veracode | Application security testing |
| Docker | Containerization |
| AWS IAM | Access management |
| AWS KMS | Encryption key management |

### Security Best Practices

- IAM least-privilege access
- Private subnet deployment
- Secure secrets management
- HTTPS/TLS communication
- Container image scanning
- Dependency vulnerability scanning
- Infrastructure security validation
- Kubernetes RBAC
- AWS resource encryption
- Secure CI/CD pipeline configuration

## 📈 Future Enhancements

- GitOps implementation using Argo CD
- Advanced monitoring using Prometheus and Grafana
- Automated vulnerability scanning with Trivy
- Blue-green deployment strategy
- Canary deployment implementation
- AWS WAF integration
- Advanced Kubernetes autoscaling
- Centralized logging and observability

## 🤝 Contributing

Contributions, suggestions, and improvements are welcome.

1. Fork the repository.
2. Create a feature branch.
3. Commit your changes.
4. Push your branch.
5. Submit a Pull Request.

## 📄 License

This project is licensed under the MIT License.

See the `LICENSE` file for details.

---

## 👨‍💻 Author & Project Links

### Vishal Chapke
**B.Tech Computer Science Student | Cloud & DevOps Enthusiast**

<p align="center">
  <a href="https://github.com/chapkevishal82-hue/cloud-native-devops-project">
    <img src="https://img.shields.io/badge/Project%20Repository-GitHub-181717?style=for-the-badge&logo=github" alt="Project Repository">
  </a>
  <a href="https://github.com/chapkevishal82-hue">
    <img src="https://img.shields.io/badge/GitHub-Profile-181717?style=for-the-badge&logo=github" alt="GitHub Profile">
  </a>
  <a href="https://linkedin.com/in/vishal-chapke-9bb3b0344/">
    <img src="https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin" alt="LinkedIn Profile">
  </a>
</p>

<p align="center">
  ⭐ Star the repository if you find it useful!
</p>

<p align="center">
  <strong>Building the future with Cloud, Automation & DevOps.</strong>
</p>

<p align="center">
  Made with ❤️ by Vishal Chapke
</p>

---

## ⭐ Support This Project

If you find this project useful:

- ⭐ Star this repository
- 🍴 Fork the repository
- 💡 Share suggestions
- 🤝 Contribute improvements
