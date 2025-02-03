---
# *Automated Node.js Deployment with Docker & Jenkins* 🚀

A **Node.js** application containerized with **Docker** and deployed using a **Jenkins CI/CD pipeline** for **automated deployment**.

---

## *📌 Project Overview*

This project demonstrates:

✅ **Building** and running a Node.js application inside a **Docker container**.

✅ **Automating CI/CD** with **Jenkins**, enabling seamless deployments.

✅ **Pushing** the Docker image to **Docker Hub**.

✅ **Deploying** the container **automatically** on each pipeline execution.

---


## *🛠 Technologies Used*

- **Node.js** – Backend runtime environment

- **Docker** – Containerization platform

- **Jenkins** – CI/CD automation tool

- **GitHub** – Version control system

---

## *📂 Project Structure*

node-docker-ci-cd/ <br>
│-- Dockerfile       # Defines the container environment <br>
│-- Jenkinsfile      # Automates CI/CD pipeline <br>
│-- package.json     # Node.js dependencies <br>
│-- index.js         # Main application file <br>
│-- README.md        # Documentation <br>

---

## 🚀 *Setup & Installation*

#### *1️⃣ Clone the Repository*
```sh
git clone https://github.com/DharmikDevops/node-docker-ci-cd.git
cd node-docker-ci-cd
```

#### *2️⃣ Run Locally (Without Docker)*
```sh
npm install
node index.js
```

✅ The application will be available at http://localhost:3000

#### *3️⃣ Run with Docker*
```sh
docker build -t dharmikmala/my-node-docker-app:latest .
docker run -d -p 3000:3000 dharmikmala/my-node-docker-app:latest
```

✅ The application will be running in a **Docker container**.

---

## *🤖 Jenkins CI/CD Pipeline*

This project includes a **Jenkinsfile** that automates:

✅ **Cloning** the repository from GitHub

✅ **Installing dependencies**

✅ **Building** a Docker image

✅ **Running tests** (Placeholder for future enhancements)

✅ **Pushing** the Docker image to **Docker Hub**

✅ **Deploying** the application automatically

---

## *🔄 Automated Deployment*

The pipeline:

**✔ Stops & removes any existing container**

**✔ Runs the new container on port 3000**


---

## *🔧 Jenkins Pipeline Execution*

1️⃣ **Add Docker Hub credentials** in Jenkins (`dockerhub-credentials`).

2️⃣ **Create a Jenkins pipeline job** and link it to this GitHub repository.

3️⃣ **Trigger the pipeline** to **automatically** build, push, and deploy the container.


---

## *📦 Docker Hub Repository*

🔹 **Docker Image:** dharmikmala/my-node-docker-app


---

## *✅ Verify Deployment*

Check if the container is running:
```
docker ps
```

Access the application at:
```
http://<server-ip>:3000
```

---
