#  Data Science Environment with Jupyter & Docker

## Overview

This project sets up a **reproducible data science environment** using Docker and Jupyter Notebook. It eliminates dependency issues by packaging Python libraries like **pandas, NumPy, and scikit-learn** into a containerized workflow.

---

##  Project Structure

```bash
jupyter-docker/
├── docker-compose.yml
├── notebooks/
└── README.md
```

---

## ⚙️ Technologies Used

* Docker
* Docker Compose
* Jupyter Notebook
* Python (pandas, NumPy, scikit-learn)

---

##  Docker Compose Configuration

### `docker-compose.yml`

```yaml
services:
  jupyter:
    image: jupyter/scipy-notebook
    ports:
      - "8888:8888"
    volumes:
      - ./notebooks:/home/jovyan/work
```

---

##  Run the Environment

Start the container using Docker Compose:

```bash
docker compose up
```

---

##  Access Jupyter Notebook

Open your browser and go to:

```text
http://localhost:8888
```

### A token will be shown in the terminal logs. Use it to log in.

---

##  Volume Mapping

```text
./notebooks → /home/jovyan/work
```

* Your local notebooks are stored in the `notebooks/` folder
* Changes are persisted outside the container

---

##  Key Concepts Demonstrated

* Reproducible data science environments
* Containerized Jupyter Notebook setup
* Volume mounting for persistent data
* Using pre-built Docker images for ML workflows

---

## Notes

* Ensure Docker and Docker Compose are installed
* First run may take time due to image download
* Default environment includes scientific Python stack


---

## ‍ Author

Pawan Kumar Panchal

