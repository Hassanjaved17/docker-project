  # Docker Backend Project

A simple Node.js backend project containerized with Docker.
This project is created for learning Docker fundamentals: Dockerfile, image building, containers, ports, and Docker commands.

## 📁 Project Structure

```text
docker-project/
├── node_modules/
├── .gitignore
├── Dockerfile
├── index.js
├── package.json
├── package-lock.json
└── README.md
```

> `node_modules` should not be copied into the Docker image. Add it to `.dockerignore`.

## 🛠️ Technologies

* Node.js 20
* npm
* Docker
* Dockerfile

## 🚀 How It Works

The Dockerfile:

1. Uses Node.js 20 as the base image.
2. Creates `/app` as the working directory.
3. Copies `package.json` and `package-lock.json`.
4. Installs project dependencies.
5. Copies the application source code.
6. Exposes port `4000`.
7. Starts the application with `node index.js`.

## 🐳 Dockerfile

```dockerfile
FROM node:20

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

EXPOSE 4000

CMD ["node", "index.js"]
```

## ▶️ Run the Project Without Docker

Install dependencies:

```bash
npm install
```

Start the backend:

```bash
node index.js
```

The application should be available on:

```text
http://localhost:4000
```

## 🐳 Build a Docker Image

Make sure Docker Desktop is running, then open the terminal inside this project:

```bash
docker build -t docker-backend .
```

Check the created image:

```bash
docker images
```

## 📦 Create and Run a Container

```bash
docker run -p 4000:4000 docker-backend
```

The application should then be available at:

```text
http://localhost:4000
```

### Run in Background

```bash
docker run -d -p 4000:4000 --name docker-backend-container docker-backend
```

## 🔍 Useful Docker Commands

List running containers:

```bash
docker ps
```

List all containers:

```bash
docker ps -a
```

View container logs:

```bash
docker logs docker-backend-container
```

Stop the container:

```bash
docker stop docker-backend-container
```

Start it again:

```bash
docker start docker-backend-container
```

Remove the container:

```bash
docker rm docker-backend-container
```

Remove the image:

```bash
docker rmi docker-backend
```

## 🧹 Recommended `.dockerignore`

Create a `.dockerignore` file:

```text
node_modules
npm-debug.log
.git
.gitignore
README.md
.env
```

This prevents unnecessary files and sensitive environment files from being copied into the Docker image.

## 🎯 Learning Goal

The purpose of this project is to understand the basic Docker workflow:

```text
Node.js Application
        ↓
    Dockerfile
        ↓
   docker build
        ↓
    Docker Image
        ↓
    docker run
        ↓
 Docker Container
        ↓
   Application
```

## ⚠️ Current Docker Desktop Issue

If Docker Desktop is stuck at **"Starting the Docker Engine..."**, the application cannot build or run containers until the Docker Engine starts successfully.

The WSL 2 setup should be checked first:

```powershell
wsl -l -v
```

Expected:

```text
Ubuntu          Stopped/Running    2
docker-desktop  Stopped/Running    2
```

Once Docker Desktop is running, verify Docker with:

```bash
docker --version
```

Then test the installation:

```bash
docker run hello-world
```

## 👨‍💻 Author

**Hassan Javed**

Learning Full Stack Web Development & Docker.
