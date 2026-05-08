# 🚀 DevSecOps CI/CD Pipeline Project

A complete end-to-end **DevSecOps CI/CD Pipeline** integrating automation, code quality analysis, security scanning, artifact management, and staging deployment using industry-standard DevOps tools.

----

# 📌 Project Overview

This project demonstrates how modern enterprise-grade CI/CD pipelines are designed with integrated security and quality validation workflows.

The pipeline automatically:

* Pulls source code from GitHub
* Triggers Jenkins via Webhook
* Performs code quality analysis using SonarQube
* Validates Quality Gates using SonarQube Webhooks
* Runs filesystem vulnerability scanning with Trivy
* Performs dependency vulnerability analysis using OWASP Dependency-Check
* Builds the application using Maven
* Publishes artifacts to Nexus Repository
* Deploys the application to a staging environment
* Sends build notifications to Slack

---

# 🏗️ Architecture Workflow

```text
GitHub Push
      ↓
GitHub Webhook
      ↓
Jenkins Pipeline
      ↓
SonarQube Analysis
      ↓
SonarQube Webhook
      ↓
Quality Gate Validation
      ↓
Trivy FileSystem Scan
      ↓
Maven Build
      ↓
OWASP Dependency Check
      ↓
Nexus Artifact Publish
      ↓
Staging Deployment
      ↓
Slack Notifications
```

---

# 🔧 Tech Stack & Tools

| Tool                   | Purpose                           |
| ---------------------- | --------------------------------- |
| Jenkins                | CI/CD Automation                  |
| GitHub Webhooks        | Automatic Pipeline Trigger        |
| SonarQube              | Code Quality & Security Analysis  |
| SonarQube Webhooks     | Quality Gate Validation           |
| Trivy                  | FileSystem Vulnerability Scanning |
| OWASP Dependency-Check | Dependency Vulnerability Analysis |
| Apache Maven           | Build & Package Management        |
| Nexus Repository       | Artifact Management               |
| Slack                  | Build Notifications               |

---

# 📂 Jenkins Pipeline Stages

## 1️⃣ Git Checkout

Pulls the latest source code from GitHub repository.

## 2️⃣ SonarQube Analysis

Performs:

* Static code analysis
* Code smell detection
* Bug detection
* Security vulnerability analysis

## 3️⃣ Quality Gate Validation

Uses SonarQube Webhooks to validate:

* Code coverage
* Security ratings
* Maintainability metrics

Pipeline fails automatically if Quality Gate conditions are not met.

## 4️⃣ Trivy FileSystem Scan

Scans the project filesystem for:

* Vulnerabilities
* Secrets
* Misconfigurations

## 5️⃣ Maven Build

Builds and packages the application using Maven.

## 6️⃣ OWASP Dependency-Check

Scans third-party dependencies for known CVEs and vulnerable libraries.

## 7️⃣ Nexus Artifact Publish

Publishes build artifacts to Nexus Repository for centralized storage and version management.

## 8️⃣ Staging Deployment

Deploys the application to the staging environment for testing.

## 9️⃣ Slack Notifications

Sends:

* Build success notifications
* Failure alerts
* Pipeline status updates

---

# 🔐 DevSecOps Features

✅ Integrated Security Scanning
✅ Automated Quality Gate Validation
✅ Vulnerability Detection
✅ Dependency Security Checks
✅ Artifact Repository Management
✅ Automated Deployment Workflow
✅ Real-Time Notifications

---

# 📸 Pipeline Screenshot
<img width="2534" height="1062" alt="flow" src="https://github.com/user-attachments/assets/771d2f2c-2e66-40ed-b852-a2de9b9df9de" />
<img width="1918" height="967" alt="Screenshot 2026-05-08 004736" src="https://github.com/user-attachments/assets/fd4e9fc3-f4ca-4752-a5a8-13be4bf17800" />
<img width="1918" height="967" alt="Screenshot 2026-05-08 004815" src="https://github.com/user-attachments/assets/3af4ef0c-9cf2-42cc-9467-5d74bb18547f" />
<img width="1918" height="966" alt="Screenshot 2026-05-08 004958" src="https://github.com/user-attachments/assets/4f33178c-67b3-46a7-87ef-e3ee4c74e15f" />
<img width="1917" height="970" alt="Screenshot 2026-05-08 004922" src="https://github.com/user-attachments/assets/8ae37d9a-8be2-4a74-af17-fe18c45975f3" />
<img width="1918" height="968" alt="Screenshot 2026-05-08 005023" src="https://github.com/user-attachments/assets/54c46a6f-01a7-497b-98c8-c9ced9dc833c" />
<img width="1918" height="900" alt="Screenshot 2026-05-08 005423" src="https://github.com/user-attachments/assets/2582955d-71da-4904-ae2a-57861456bc96" />










---

# 🚀 Future Enhancements

* Docker Integration
* Kubernetes Deployment
* ArgoCD GitOps Workflow
* Prometheus Monitoring
* Grafana Dashboards
* Trivy Container Image Scanning
* Automated Infrastructure Provisioning

---

# 📖 Learning Outcomes

Through this project, I gained hands-on experience in:

* CI/CD Pipeline Automation
* DevSecOps Best Practices
* Secure Software Delivery
* Jenkins Pipeline Development
* Artifact Management
* Security & Vulnerability Scanning
* Enterprise Deployment Workflows

---

# 🤝 Connect With Me

If you found this project interesting, feel free to connect and share feedback!

⭐ Star this repository if you like the project.
