# Flask + MySQL Docker Compose Project

## Overview

This project is a simple multi-container application using:

* Flask (Python web app)
* MySQL (database)
* Docker Compose (to run both services together)

The Flask app connects to the MySQL container and returns a message.

---

## Project Structure

```
03-Flask-application/
├── app.py
├── Dockerfile
├── docker-compose.yml
└── requirements.txt
```

---

## Requirements

* Docker
* Docker Compose (v2 → `docker compose`)

---

## Setup & Run

### 1. Start the application

```
docker compose up --build
```

### 2. Run in background (optional)

```
docker compose up --build -d
```

---

## Access the Application

```
http://localhost:5000
```

or

```
curl http://<server-ip>:5000
```

---

## Database Details

* Host: `db`
* User: `root`
* Password: `password`
* Database: `test_db`

---

## Access MySQL Container

```
docker compose exec db mysql -u root -p
```

Password:

```
password
```

---

## Useful Commands

### Check containers

```
docker compose ps
```

### View logs

```
docker compose logs web
docker compose logs db
```

### Stop containers

```
docker compose down
```

---

## Notes

* Flask connects to MySQL using service name `db`
* Both containers run on the same Docker network
* MySQL data is stored using a Docker volume (`db_data`)

---

## Dependencies (requirements.txt)

```
flask
mysql-connector-python
```

