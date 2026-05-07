# Reduce Docker Image Size for Python Application

This project demonstrates how to optimize and reduce the Docker image size for a Python application using:

- Multi-stage Docker builds
- Alpine Linux
- Lightweight runtime containers

The application reads CSV data using the Pandas library and displays a preview of the dataset.

---

# Technologies Used

- Docker
- Python 3.9
- Pandas
- Alpine Linux

---

# Project Structure

```bash
redece_image/
├── data.csv
├── dockerfile
├── requirements.txt
└── script.py
```

---

# Python Script

## `script.py`

```python
import pandas as pd

df = pd.read_csv("data.csv")

print("Dataset Preview:")
print(df.head())
```

---

# Dataset File

## `data.csv`

```csv
id,name,age
1,Panchal,25
2,Rahul,26
3,Aman,24
4,Riya,23
5,Sneha,22
```

---

# Requirements File

## `requirements.txt`

```txt
pandas==2.2.2
```

---

# Dockerfile

## `dockerfile`

```Dockerfile
# stage 1 : Build

from python:3.9-alpine as build

workdir /app

copy requirements.txt .

run pip install --no-cache-dir --prefix=/install -r requirements.txt

copy script.py .
copy data.csv .

# stage 2 : Run

from python:3.9-alpine

workdir /app

COPY --from=build /install /usr/local
copy --from=build /app /app

cmd ["python", "script.py"]
```

---

# Build Docker Image

Run the following command to build the Docker image:

```bash
docker build -t optimized-python-app -f dockerfile .
```

---

# Run Docker Container

```bash
docker run optimized-python-app
```

---

# Expected Output

```bash
Dataset Preview:
   id     name  age
0   1  Panchal   25
1   2    Rahul   26
2   3     Aman   24
3   4     Riya   23
4   5   Sneha   22
```

---

# Optimization Techniques Used

| Technique | Description |
|------------|-------------|
| Alpine Linux | Uses a lightweight base image |
| Multi-stage Build | Separates build and runtime stages |
| `--no-cache-dir` | Prevents pip cache storage |
| Minimal Runtime | Reduces final image size |

---

# Benefits

- Smaller Docker image size
- Faster container startup
- Reduced storage usage
- Better performance
- Production-friendly container setup

---

# Verify Image Size

```bash
docker images
```

---

# Author

Pawan Kumar Panchal  
Cloud Engineer | DevOps Learner
