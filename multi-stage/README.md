# Node.js Multi-Stage Docker Application

## Overview

This project demonstrates how to containerize a simple Node.js application using a **multi-stage Docker build**. The goal is to separate the build environment from the runtime environment to create a **smaller, optimized production image**.

---

## Project Structure

```bash
multi-stage/
├── server.js
├── package.json
├── Dockerfile
└── README.md
```

---

## Application Details

* Built with **Node.js** and **Express**
* Runs a simple HTTP server
* Returns a message:
  `Hello from Node.js`

---

## Docker Multi-Stage Build

The Dockerfile uses two stages:

### Stage 1: Build Stage

* Uses full Node.js image
* Installs dependencies (`npm install`)
* Prepares the application

### Stage 2: Runtime Stage

* Uses lightweight Node.js image (`node:slim`)
* Copies only required files:

  * `server.js`
  * `node_modules`
* Runs the application

---

## Build the Image

```bash
docker build -t node-multi-stage .
```

---

## Run the Container

```bash
docker run -d -p 3000:3000 node-multi-stage
```

---

## Access the Application

```bash
http://localhost:3000
```

or

```bash
curl http://<server-ip>:3000
```

---

## Expected Output

```text
Hello from Node.js
```

---

## Key Concepts Demonstrated

* Multi-stage Docker builds
* Dependency management with `package.json`
* Optimized container images
* Port exposure and container networking

---

## Notes

* Application listens on `0.0.0.0:3000` for external access
* Dependencies are installed during Docker build, not on host
* Image is optimized by excluding unnecessary build files

---

## Author

Pawan Kumar Panchal

