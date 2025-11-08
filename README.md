# 🏋️ ACEest Fitness & Gym — DevOps CI/CD Pipeline

## 📘 Project Overview
**ACEest Fitness & Gym** is a digital transformation initiative for a modern fitness startup.  
This project demonstrates a **fully automated DevOps CI/CD pipeline** built around the organization’s core Flask-based web application. The pipeline ensures continuous integration, testing, code quality validation, and automated containerized deployment using modern DevOps tools.

---

## 🚀 Objectives
- Apply DevOps principles to design and automate the end-to-end CI/CD lifecycle.
- Integrate modern tools like **GitHub**, **Jenkins**, **SonarQube**, **Pytest**, **Docker**, and **Kubernetes**.
- Implement quality validation, containerization, and automated deployments with rollback mechanisms.

---

## 🧩 Tech Stack & Tools

| Category | Tool / Framework | Purpose |
|-----------|------------------|----------|
| **Version Control** | Git + GitHub | Code versioning and collaboration |
| **Build Automation** | Jenkins | Continuous Integration (CI) |
| **Testing** | Pytest | Unit and integration testing |
| **Code Quality** | SonarQube | Static code analysis and quality gates |
| **Containerization** | Docker / Podman | Application packaging |
| **Container Registry** | Docker Hub / Quay.io | Image storage and versioning |
| **Orchestration** | Kubernetes / Minikube | Continuous Delivery (CD) |
| **Programming Language** | Python (Flask) | Core web application |

---

## ⚙️ CI/CD Pipeline Workflow

### 1. **Version Control (Git + GitHub)**
- Initialize repo: `git init`
- Branching strategy: `main` for stable releases, `dev` for active development.
- Use semantic versioning (e.g., `v1.1`, `v1.2.3`).

---

### 2. **Continuous Integration (Jenkins)**
- Jenkins polls GitHub for changes (`SCM Poll` or Webhook).
- Triggers the following stages:

```
Stage 1: Checkout Code
Stage 2: Install Dependencies
Stage 3: Run Pytest
Stage 4: SonarQube Code Analysis
Stage 5: Build Docker Image
Stage 6: Push to Docker Hub
Stage 7: Deploy to Kubernetes
```

---

### 3. **Automated Testing (Pytest)**
- Each commit triggers automated tests.
- Test results are shown in Jenkins console output and stored as artifacts.

---

### 4. **Code Quality (SonarQube)**
- Integrated into Jenkins pipeline.
- Enforces code quality gates: maintainability, code smells, coverage, and vulnerabilities.

---

### 5. **Containerization (Docker / Podman)**
- Flask app is packaged into a Docker image with dependencies.
- Images are versioned and pushed to Docker Hub:
  ```bash
  docker build -t aceestfitness:v1.3 .
  docker push <your-dockerhub-username>/aceestfitness:v1.3
  ```

---

### 6. **Continuous Delivery (Kubernetes / Minikube)**
- Deployed via Kubernetes manifests.
- Supports deployment strategies:
  - **Blue-Green Deployment**
  - **Canary Release**
  - **Rolling Update**
  - **A/B Testing**
  - **Shadow Deployment**
- Rollback supported in case of deployment failure.

---

## 🧪 Testing

Run locally before pushing:
```bash
pytest -v
```

Check SonarQube analysis:
```bash
sonar-scanner -Dsonar.projectKey=ACEest_Fitness
```

---

## 🐳 Docker Usage

**Build and Run Locally:**
```bash
docker build -t aceest-fitness:v1.3 .
docker run -d -p 5000:5000 aceest-fitness:v1.3
```

**Push to Docker Hub:**
```bash
docker tag aceest-fitness:v1.3 <your-dockerhub-username>/aceest-fitness:v1.3
docker push <your-dockerhub-username>/aceest-fitness:v1.3
```

---

## ☸️ Kubernetes Deployment

**Deploy Application:**
```bash
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml
```

**Check Deployment Status:**
```bash
kubectl get pods
kubectl get svc
```

---

## 🧠 Challenges & Mitigations
| Challenge | Mitigation |
|------------|-------------|
| Jenkins-SonarQube integration errors | Configured webhook and authentication token properly |
| Container build failures | Used multi-stage builds and cached dependencies |
| Test environment isolation | Implemented tests inside Docker container |
| Kubernetes rollback | Added versioned image tags and rollback script |

---

## 🧾 Author
**Name:** *Sindhu*  
 
