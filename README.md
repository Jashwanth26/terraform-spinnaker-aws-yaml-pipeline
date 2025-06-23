# Spinnaker AWS YAML Pipeline

A production-grade CI/CD pipeline using **Spinnaker** deployed on **AWS ECS**, managed purely with **YAML configs** — no Halyard involved.

This project demonstrates:
- 🚀 Dockerized Spinnaker microservices (`clouddriver`, `deck`, `gate`, `orca`, `echo`, etc.)
- ⚙️ CI with **GitHub Actions** (build, test, push to ECR)
- 🚢 CD with **Spinnaker Pipelines** (trigger, deploy to ECS)
- 📦 Image storage in **Amazon ECR**
- 🧠 Redis (Elasticache) caching for Spinnaker services
- 🧱 Infra provisioned using **Terraform**

---

## 📁 Project Structure

```
.
├── terraform/                   # ECS, Redis, ECR, ALB provisioning
├── clouddriver/
│   ├── application.yml          # YAML configuration for AWS, ECS, Redis
│   └── Dockerfile
├── deck/
│   ├── settings-local.js        # UI service configuration
│   └── Dockerfile
├── .github/workflows/
│   └── ci.yml                   # GitHub Actions CI pipeline
├── README.md
```

---

## 🛠️ Prerequisites

- AWS account
- Terraform installed
- Docker installed
- GitHub Actions enabled with ECR role access

---

## 🚀 Quick Start

```bash
# 1. Clone repo
$ git clone https://github.com/your-username/spinnaker-aws-yaml-pipeline.git

# 2. Deploy infrastructure (ECS, Redis, etc.)
$ cd terraform
$ terraform init && terraform apply

# 3. Build Docker image
$ cd ../clouddriver
$ docker build -t clouddriver:custom .

# 4. Push image to ECR (handled by GitHub Actions on push)
```

---

## 🔁 GitHub Actions CI Workflow

`.github/workflows/ci.yml` includes:
- Gradle build & test
- Docker build
- Push image to Amazon ECR using OIDC

---

## 📦 Spinnaker CD Pipeline
- Pipeline is defined via `front50`
- Deploys ECR image to ECS task
- Region: `ap-south-1`
- Fully visible in Spinnaker UI

![Pipeline UI Screenshot](./screenshots/pipeline-ui.png)

---

## 🧠 Concepts Demonstrated
- Dockerized Spinnaker without Halyard
- YAML-config-driven deployments
- GitHub Actions OIDC to AWS ECR
- ECS blue/green deployment via Spinnaker

---

## 📌 Future Enhancements
- Argo CD or Flux alternative comparison
- Add Prometheus + Grafana for observability
- Automated pipeline config deployment via Terraform

---

## 📣 Connect
Like this project? Star ⭐ it or share your feedback.  
Tweet your thoughts and tag me on [X/Twitter](https://x.com/JashwanthJakku5)

---
