# 🌐 Basic Kubernetes Web Application Deployment — Docker + K8S

Welcome to the **Web Application Deployment Project** using **Docker** and **Kubernetes** 🚀
This repository contains everything needed to build, package, and deploy a complete web application on a Kubernetes cluster.

<img width="1342" height="563" alt="image" src="https://github.com/user-attachments/assets/23d91e15-1e45-4530-94ac-9c4e723f8af6" />


The project is beginner-friendly and designed to help you understand **Docker**, **Kubernetes**, and **basic DevOps workflows** step by step.

---

## 📁 Project Overview

This project deploys a simple static web application using:

* 🐳 **Docker** (Apache Web Server)
* ☸️ **Kubernetes Deployment**
* 🌍 **Kubernetes Service (LoadBalancer)**
* ☁️ **AWS EC2 Ubuntu Server** (optional, but used here)
* 🔐 **GitHub with SSH authentication**

Website files are packaged inside a `.tar.gz` archive and extracted during the Docker image build process.

---

## 🧱 Project Structure

```bash
webapp-k8s/
│── docker/
│   └── Dockerfile
│
│── k8s/
│   ├── deployment.yaml
│   ├── service.yaml
│
│── webimg12.tar.gz         # Website source files
│── README.md               # Project documentation
```

---

## 🐳 Docker Setup

### 🔨 1. Build the Docker Image

```bash
docker build -t webapp:v1 ./docker
```

### ▶️ 2. Run the Container Locally

```bash
docker run -d -p 8080:80 webapp:v1
```

### 🔍 3. Test in Browser

Open your browser and visit:

```
http://<your-ip>:8080
```

You should see your website running successfully 🎉

---

## ☸️ Kubernetes Deployment

This project includes ready-to-use Kubernetes manifests.

### 📌 1. Deploy the Application

```bash
kubectl apply -f k8s/deployment.yaml
```

### 📌 2. Expose the Application

```bash
kubectl apply -f k8s/service.yaml
```

### 📌 3. Verify Resources

```bash
kubectl get pods
kubectl get deploy
kubectl get svc
```

#### Accessing the Application

* **Cloud Providers (AWS / GCP / Azure):**
  Open the `EXTERNAL-IP` from the service output in your browser.

* **Minikube:**

  ```bash
  minikube service webapp-service
  ```

---

## 🚀 How the Application Works

### ✔️ Dockerfile

* Installs Apache Web Server
* Extracts website files from `webimg12.tar.gz`
* Copies files to `/var/www/html/`
* Runs Apache in the foreground

### ✔️ Kubernetes Deployment

* Runs multiple replicas of the web application
* Provides high availability and self-healing

### ✔️ Kubernetes Service

* Exposes the application on port `80`
* Load balances traffic across pods

---

## 🔐 SSH Authentication to GitHub

To push this project securely to GitHub using SSH:

```bash
ssh-keygen -t ed25519 -C "your-email"
ssh-add ~/.ssh/id_ed25519
git remote set-url origin git@github.com:<username>/<repository>.git
git push -u origin main
```

---

## ✨ What You Learn From This Project

✔ Writing a Dockerfile
✔ Packaging a website into a Docker image
✔ Deploying applications using Kubernetes
✔ Exposing applications using Kubernetes Services
✔ Pushing code to GitHub using SSH authentication
✔ Structuring real-world DevOps projects efficiently

---

## 📌 Conclusion

This project provides a complete **Docker → Kubernetes → Cloud** deployment workflow and is a strong foundation for DevOps and Cloud-Native learning.

Happy Deploying! 🚀
