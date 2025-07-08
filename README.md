# 🐳 MongoDB + Mongo Express on Kubernetes

This project deploys **MongoDB** and **Mongo Express** using Kubernetes on **Minikube**. It demonstrates using:
- Deployments
- Services
- ConfigMaps
- Secrets
- Minikube tunnels for local access

---

## 🧱 Components

### 1. **MongoDB Deployment**
- Deploys a MongoDB container
- Uses a Kubernetes `Secret` to set root username and password
- Exposes port `27017`

### 2. **Mongo Express Deployment**
- UI for managing MongoDB
- Connects to MongoDB using:
  - Secrets for auth
  - ConfigMap for service URL
- Exposes port `8081`

### 3. **Kubernetes Resources Used**
- `Deployment`: For running MongoDB and Mongo Express pods
- `Service`: For internal (MongoDB) and external (NodePort) communication
- `Secret`: For secure credentials
- `ConfigMap`: To configure Mongo Express with the MongoDB service URL

---

## 📂 Project Structure
├── mongodb-deployment.yaml # MongoDB Deployment <br>
├── mongo-express-deployment.yaml # Mongo Express Deployment <br>
├── mongodb-service.yaml # MongoDB Service (ClusterIP)<br>
├── mongo-express-service.yaml # Mongo Express Service (NodePort)<br>
├── mongodb-secret.yaml # Kubernetes Secret (username/password)<br>
└── mongodb-configmap.yaml # ConfigMap with MongoDB service reference<br>



---

## 🚀 Getting Started

### 🧰 Prerequisites

Make sure the following are installed:

- [Minikube](https://minikube.sigs.k8s.io/docs/start/)
- [kubectl](https://kubernetes.io/docs/tasks/tools/)
- [Git](https://git-scm.com/)

---

### 📦 Step-by-Step Setup

#### 1. Start Minikube

```bash
minikube start
```
#### 2. Clone the Repository
git clone https://github.com/Nikhilg23/Mongo-K8-setup.git
cd mongo-k8s-setup

#### 3. Apply All YAML Files
```bash
kubectl apply -f .
```

## 🌐 Access Mongo Express UI
```bash
minikube service mongo-express-service
```

## 🔐 Credentials

| Component        | Username                     | Password   |
| ---------------- | ---------------------------- | ---------- |
| MongoDB          | `username`                   | `password` |
| Mongo Express UI | admin/pass (optional config) |            |

Stored securely in mongodb-secret.yaml using base64 encoding.
```bash
echo -n 'your-value' | base64
```
