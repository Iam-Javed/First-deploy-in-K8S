🌐 #Kubernetes WebApp Deployment — End‑to‑End Project
Welcome to my Web Application Deployment Project using Docker + Kubernetes!
This repository contains everything needed to build, package, and deploy a complete web application on a Kubernetes cluster.
This project is designed to be easy to understand, even if you're new to Docker or Kubernetes.
Let's dive in 🚀

📁 #Project Overview
This project deploys a simple web application on:

Docker (Apache web server)
Kubernetes Deployment
Kubernetes Service (LoadBalancer)
AWS EC2 Ubuntu Server (optional but used here)
GitHub with SSH authentication

The website files are packaged inside a .tar.gz file and extracted inside the Docker image.

🧱 #Project Structure
webapp-k8s/
│── docker/
│   └── Dockerfile
│
│── k8s/
│   ├── deployment.yaml
│   ├── service.yaml
│   ├── ingress.yaml        (optional)
│   ├── namespace.yaml      (optional)
│   └── configmap.yaml      (optional)
│
│── webimg12.tar.gz         # Website source files
│── README.md               # You're reading this file :)


🐳 #Docker Setup
🔨 1. Build the Docker Image
Shelldocker build -t webapp:v1 ./dockerShow more lines
▶️ 2. Run the Container Locally
Shelldocker run -d -p 8080:80 webapp:v1Show more lines
🔍 3. Test in Browser
Open:
http://yourIP:8080

You should see your website running!

☸️ #Kubernetes Deployment
This project includes ready‑to‑use Kubernetes manifests.
📌 1. Deploy the Application
Shellkubectl apply -f k8s/deployment.yamlShow more lines
📌 2. Expose the Application
Shellkubectl apply -f k8s/service.yamlShow more lines
📌 3. Check Resources
Shellkubectl get podskubectl get deploykubectl get svcShow more lines
If you're using AWS / GCP / Azure:
Service → EXTERNAL-IP → Open in browser

If you're using Minikube:
>> Shell
minikube service webapp-serviceShow more lines

🚀 #How the Application Works
✔️ The Dockerfile:

Installs Apache
Extracts website files from webimg12.tar.gz
Stores them in /var/www/html/
Runs Apache in the foreground

✔️ The Kubernetes Deployment:

Runs multiple replicas of the web application
Ensures high availability and self‑healing

✔️ The Service:

Exposes the app on port 80
Load balances traffic across pods


🔐 # SSH Authentication to GitHub (Used in this Project)
To push this project securely:
>> Shell
ssh-keygen -t ed25519 -C "your-email"ssh-add ~/.ssh/id_ed25519git remote set-url origin git@github.com:<username>/<repo>.git
git push -u origin main

🧪 # Testing & Troubleshooting
Check pod logs
kubectl logs <pod-name>Show more lines
Restart pods
kubectl delete pod <pod-name>Show more lines
Describe pods (to see events)
Shellkubectl describe pod <pod-name>Show more lines

✨ # What You Learn From This Project
✔ How to write a Dockerfile
✔ How to package a website into a Docker image
✔ How to deploy apps using Kubernetes
✔ How to expose apps using Services
✔ How to push code to GitHub using SSH keys
✔ How to efficiently structure DevOps projects
