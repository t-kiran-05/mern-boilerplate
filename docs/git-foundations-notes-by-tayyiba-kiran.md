
## 🚀 Project Setup Notes

### 📁 Folder Structure

```
/
├── client/               # Frontend (React)
│   └── Dockerfile
├── server/               # Backend (Node.js + PM2)
│   └── Dockerfile
├── docker-compose.yml
├── .env.example
├── .gitignore
├── .dockerignore
├── README.md
└── package.json
```

---

### ✅ What I Updated

#### 1. **Dockerfile (Client)**

* Used Node to build the React app.
* Used Nginx to serve the static files.
* Final image is very small and fast.

#### 2. **Dockerfile (Server)**

* Used Node 16 Alpine image.
* Installed PM2 globally to run the server.
* Used `pm2-runtime` in the `CMD`.

#### 3. **.gitignore**

* Ignored:

  * node\_modules
  * build/
  * env files (except example)
  * log files
  * editor and OS-specific files

#### 4. **.env.example**

* Added placeholder values for both client and server environments.

#### 5. **docker-compose.yml**

* Added setup for `client` and `server` services.
* Linked everything to work together.

#### 6. **package.json**

* Added scripts to build Docker images for ARM (Apple Silicon, Raspberry Pi etc):

```json
"scripts": {
  "docker:build:client:arm": "docker buildx build --platform linux/arm64 -t mdp-client-arm ./client",
  "docker:build:server:arm": "docker buildx build --platform linux/arm64 -t mdp-server-arm ./server"
}
```

---

### 💻 Git Commands Used

```bash
git add .
git commit -m "Updated Dockerfiles, envs, ignore files and added ARM build script"
git push
```

---

by Tayyiba Kiran







																																																																																																x

