# cicd-demo

# CI/CD Pipeline with Docker and GitHub Actions

## 📌 Project Overview
This project demonstrates a complete **CI/CD pipeline** for a Python Flask application using **GitHub Actions**, **Docker**, and deployment on an **Azure Virtual Machine**.  
The pipeline automates code testing, Docker image creation, pushing the image to **Docker Hub**, and running the containerized application on a cloud VM, accessible via an external browser.

---

## 🛠️ Tech Stack
- **Programming Language:** Python (Flask)
- **Version Control:** Git & GitHub
- **CI/CD Tool:** GitHub Actions
- **Containerization:** Docker
- **Container Registry:** Docker Hub
- **Cloud Platform:** Microsoft Azure (Linux VM)
- **OS:** Ubuntu

---

## 🧩 Architecture Flow
Developer → GitHub Repo → GitHub Actions (CI/CD)→ Docker Image Build→ Docker Hub→ Azure VM→ External Browser Access

---

## ⚙️ CI/CD Pipeline Workflow
The CI/CD pipeline is triggered on every push to the `main` branch.

### ✅ Build Job
- Checkout source code
- Login to Docker Hub securely using GitHub Secrets
- Build Docker image from Dockerfile
- Tag the image as `latest`
- Push the image to Docker Hub

### ✅ Test Job
- Runs after successful build
- Sets up Python environment
- Installs dependencies
- Executes unit tests using `pytest`

---

## 🐳 Dockerization
- Flask application is containerized using Docker
- The app runs on port `8080`
- Docker image is lightweight and portable

**Dockerfile highlights:**
- Base image: `python:3.8`
- Exposes port `8080`
- Runs Flask app using `python app.py`

---

## ☁️ Deployment on Azure VM
- Docker installed on Azure Linux VM
- Docker image pulled from Docker Hub
- Container started with port mapping:
  ```bash
  docker run -d -p 8080:8080 snikhil1729/my-image:latest
-Azure Network Security Group (NSG) configured to allow inbound traffic on port 8080

🌐 Application Access
The application can be accessed from an external browser using:
http://<AZURE_VM_PUBLIC_IP>:8080

Output:
Hello CICD World!

*“This project demonstrates an end‑to‑end CI/CD workflow. I used GitHub Actions to automate the pipeline. On every push to the main branch, the pipeline checks out the code, runs unit tests using pytest, builds a Docker image using a Dockerfile, and pushes the image to Docker Hub securely using GitHub Secrets.*
>
> *On the deployment side, I provisioned an Azure Linux VM, installed Docker, pulled the image from Docker Hub, and ran it as a container with port mapping. I configured Azure NSG rules to allow external traffic, which allowed me to access the Flask application through a public IP. The application returns a simple response — ‘Hello CICD World!’ — confirming successful deployment.”*
