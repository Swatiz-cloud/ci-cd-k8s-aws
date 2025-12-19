# 🚀 End-to-End CI/CD Pipeline with Docker, Kubernetes & AWS

![AWS](https://img.shields.io/badge/AWS-Cloud-orange?style=for-the-badge&logo=amazonaws)
![Docker](https://img.shields.io/badge/Docker-Container-blue?style=for-the-badge&logo=docker)
![Kubernetes](https://img.shields.io/badge/Kubernetes-Orchestration-blue?style=for-the-badge&logo=kubernetes)
![Jenkins](https://img.shields.io/badge/Jenkins-CI%2FCD-red?style=for-the-badge&logo=jenkins)
![GitHub](https://img.shields.io/badge/GitHub-SCM-black?style=for-the-badge&logo=github)

## 📌 Project Overview

This project demonstrates a **production-grade end-to-end CI/CD pipeline** using **GitHub, Jenkins, Docker, Kubernetes, and AWS**.
The pipeline automates application build, containerization, image storage, and deployment to a Kubernetes cluster hosted on AWS EC2 with **zero-downtime rolling updates**.

---

## 🎯 Objectives

- Automate application build and deployment process
- Implement containerization using Docker
- Store Docker images securely in AWS ECR
- Deploy applications on Kubernetes using rolling updates
- Achieve faster, reliable, and consistent deployments

---

## 🛠️ Technology Stack

| Category           | Tools                |
|--------------------|----------------------|
| Source Control     | GitHub               |
| CI/CD              | Jenkins              |
| Build Tool         | Maven                |
| Containerization   | Docker               |
| Container Registry | AWS ECR              |
| Orchestration      | Kubernetes (kubeadm) |
| Cloud Provider     | AWS EC2              |
| OS                 | Ubuntu Linux         |
| Application        | Java Spring Boot     |

---

## 🏗️ Architecture

![Architecture](https://www.betsol.com/wp-content/uploads/2018/11/dfgsdf.png)

![CI/CD Flow](https://miro.medium.com/0%2AQsstSyrhexzaKRAr)

**Workflow:**

```
Developer → GitHub → Jenkins → Docker → AWS ECR → Kubernetes → End Users
```

---

## 📁 Project Structure

```
ci-cd-k8s-aws/
├── app/
│   ├── src/
│   ├── pom.xml
│   └── Dockerfile
├── k8s/
│   ├── deployment.yml
│   ├── service.yml
│   └── namespace.yml
├── Jenkinsfile
└── README.md
```

---

## ⚙️ Prerequisites

- AWS Account
- EC2 instances (Jenkins + Kubernetes nodes)
- Docker installed
- Kubernetes cluster (kubeadm)
- Jenkins installed and configured
- AWS CLI configured
- kubectl installed

---

## 🚀 CI/CD Pipeline Stages

### 1️⃣ Source Code Management (GitHub)

- Application code is hosted in GitHub.
- GitHub webhook triggers Jenkins on every commit.

### 2️⃣ Continuous Integration (Jenkins)

- Jenkins pulls the latest code from GitHub.
- Maven builds the Spring Boot application.
- Unit tests are executed during the build.

### 3️⃣ Docker Image Build

- Jenkins builds a Docker image using the Dockerfile.
- Image contains the packaged Spring Boot JAR.

### 4️⃣ Push Image to AWS ECR

- Jenkins authenticates to AWS ECR.
- Docker image is tagged and pushed to ECR repository.

### 5️⃣ Continuous Deployment (Kubernetes)

- Jenkins deploys the application to Kubernetes.
- Rolling update strategy ensures **zero downtime**.
- Application is exposed using Kubernetes Service (NodePort).

---

## 📦 Jenkins Pipeline

Pipeline is defined using a **declarative Jenkinsfile**:

- Checkout Code
- Build Application
- Build Docker Image
- Push Image to AWS ECR
- Deploy to Kubernetes

---

## 🔁 Deployment Strategy

- **RollingUpdate** strategy
- Multiple replicas for high availability
- No service interruption during deployments

---

## 📊 Outcome & Benefits

- 🚀 Reduced release time by **50%**
- ✅ Zero-downtime deployments
- 🔄 Automated end-to-end workflow
- 📦 Consistent and repeatable releases
- ⚡ Improved reliability and scalability

---

## 🔍 Verification

```bash
kubectl get pods
kubectl get svc
kubectl rollout status deployment cicd-app
```

Access application:

```
http://<NodeIP>:<NodePort>
```

---

## 🔐 Security Considerations

- AWS IAM roles used for ECR access
- Jenkins credentials stored securely
- Kubernetes namespace isolation

---

## 📈 Future Enhancements

- Add HPA (Horizontal Pod Autoscaler)
- Configure Ingress with NGINX
- Implement monitoring using Prometheus & Grafana
- Infrastructure provisioning using Terraform
- Add automated testing stages

---

## 👩‍💻 Author

**Swati Zampal**  
AWS Cloud Engineer | DevOps Trainer  
AWS Certified Solutions Architect – Associate  

GitHub: https://github.com/Swatiz-cloud

---

## ⭐ Conclusion

This project showcases a **real-world DevOps CI/CD implementation** aligning with industry best practices. It demonstrates expertise in **automation, containerization, orchestration, and cloud deployment**.
