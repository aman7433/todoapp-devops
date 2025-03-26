# Django Todo App (DevOps Edition)

A simple **Django-based Todo App**, containerized using **Docker** and automated with **GitHub Actions**.

 🚀 Features
- **Django-based Todo App** 📝
- **Dockerized for Easy Deployment** 🐳
- **Automated Deployment with GitHub Actions** ⚡
- **CloudWatch Logging Integration** 📊 (AWS setup required)

---

 🛠 Setup & Installation

### 1️⃣ Clone the Repository
```bash
$ git clone https://github.com/aman7433/todoapp-devops.git
$ cd todoapp-devops
```

### 2️⃣ Run with Docker

 a) Build and Run the Container
```bash
$ docker build -t todoapp .
$ docker run -d -p 8000:8000 --name todoapp todoapp
```
App will be available at: **http://127.0.0.1:8000/todos**

 b) Check Container Logs
```bash
$ docker logs -f todoapp
```

 c) Stop and Remove Container
```bash
$ docker stop todoapp
$ docker rm todoapp
```

---

## 🔄 Running Migrations
```bash
$ docker exec -it todoapp python manage.py makemigrations
$ docker exec -it todoapp python manage.py migrate
```

### 🏗 Create Superuser (Admin Access)
```bash
$ docker exec -it todoapp python manage.py createsuperuser
```

---

## 🌐 Running with GitHub Actions (CI/CD)
### **Automated Deployment Pipeline**
This repository includes a **GitHub Actions workflow** that automates building and deploying the Dockerized app.

- **Push to GitHub → Build & Deploy Automatically 🚀**
- **Custom AWS/Cloud Logging Supported**

#### ✅ **To Trigger Deployment:**
1. Push changes to the `main` branch
2. GitHub Actions will build and deploy automatically

---

## 📜 Environment Variables
Create a `.env` file and configure necessary values:
```env
SECRET_KEY=your-secret-key
DEBUG=True
DATABASE_URL=sqlite:///db.sqlite3
```

---

## 📡 Cloud Logging (AWS CloudWatch)
To enable **AWS CloudWatch logging** for this app inside Docker:

```bash
$ docker run -d \
  --log-driver=awslogs \
  --log-opt awslogs-region=us-east-1 \
  --log-opt awslogs-group=/todoapp/logs \
  --log-opt awslogs-stream=todoapp-container \
  -p 8000:8000 todoapp
```

🔹 **Ensure AWS CLI is installed and configured before using AWS logs.**

---



