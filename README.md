🏋️‍♂️ Fitness App — DevOps Project
A full-stack Fitness Application deployed using Docker, Kubernetes, and Minikube.
This project includes a Node.js backend, a HTML/CSS frontend, and complete Kubernetes deployment manifests.
🚀 Features
🔧 DevOps Stack
Dockerized frontend & backend
Kubernetes:
Deployment
Service (NodePort)
Minikube local cluster setup
Auto-deployment after changes (docker build → push → kubectl rollout restart)
🖥 App Stack
Backend → Node.js + Express
Frontend → Simple HTML/CSS/JS
API for basic fitness data example
📁 Project Structure
Fitness-App/
│
├─ docker/
│  ├─ backend/
│  │   ├─ Dockerfile
│  │   ├─ index.js
│  │   └─ package.json
│  │
│  └─ frontend/
│      ├─ Dockerfile
│      └─ index.html
│
├─ k8s/
│  ├─ backend-deployment.yaml
│  ├─ backend-service.yaml
│  ├─ frontend-deployment.yaml
│  └─ frontend-service.yaml
│
└─ README.md

🐳 Docker Setup
1️⃣ Build images
Backend:
docker build -t h4meed/fitness-backend:latest docker/backend/
Frontend:
docker build -t h4meed/fitness-frontend:latest docker/frontend/

2️⃣ Push images to Docker Hub
docker push h4meed/fitness-backend:latest
docker push h4meed/fitness-frontend:latest
☸️ Kubernetes Setup
1️⃣ Start Minikube
minikube start
2️⃣ Apply backend manifests
kubectl apply -f k8s/backend-deployment.yaml
kubectl apply -f k8s/backend-service.yaml
3️⃣ Apply frontend manifests
kubectl apply -f k8s/frontend-deployment.yaml
kubectl apply -f k8s/frontend-service.yaml

🌐 Access the App
Check service URLs:
Backend:
minikube service fitness-service
Frontend:
minikube service fitness-frontend-service
You will get URLs like:
http://127.0.0.1:<port>
Note:
On Mac (Docker driver), Minikube opens a tunnel, so the URL will be localhost with a random port.

🔁 Updating the App After Code Changes
When you change frontend or backend code:
Step 1 — Rebuild image
docker build -t h4meed/fitness-frontend:latest docker/frontend/
docker build -t h4meed/fitness-backend:latest docker/backend/
Step 2 — Push to Docker Hub
docker push h4meed/fitness-frontend:latest
docker push h4meed/fitness-backend:latest
Step 3 — Restart the deployment
Frontend:
kubectl rollout restart deployment/fitness-frontend
Backend:
kubectl rollout restart deployment/fitness-app
Pods will restart and pull the latest images.

📸 Screenshots (Optional — Add if you want)
[ Add frontend UI screenshot here ]
🧠 Learning Outcomes (Good for your resume)
This project demonstrates:
✔ Docker image creation
✔ Pushing to Docker Hub
✔ Kubernetes deployments + services
✔ Minikube cluster management
✔ Exposing apps via NodePort
✔ Rolling updates with kubectl rollout restart
Perfect for SRE / DevOps interviews!

🏁 Final Notes
You can extend this project by adding:
Ingress + domain
ConfigMaps & Secrets
CI/CD (GitHub Actions or Jenkins)
MongoDB backend
Prometheus + Grafana monitoring

