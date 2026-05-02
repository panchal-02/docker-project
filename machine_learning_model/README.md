#  TensorFlow Model Dockerization

##  Overview

This project demonstrates how to **containerize a machine learning model using TensorFlow** with Docker. The goal is to create a **portable and reproducible environment** so the model can run consistently across different systems without manual setup.

---

##  Project Structure

```bash
tensorflow-docker/
├── model.py
├── Dockerfile
└── README.md
```

---

## ⚙️ Technologies Used

* Python
* TensorFlow
* Docker

---

##  Application Description

The application loads a **pre-trained MobileNetV2 model** from TensorFlow and verifies successful initialization.

### `model.py`

```python
import tensorflow as tf

model = tf.keras.applications.MobileNetV2(weights='imagenet')
print("Model loaded successfully")
```

---

##  Docker Configuration

### Dockerfile

```dockerfile
FROM tensorflow/tensorflow:latest

WORKDIR /app

COPY . .

CMD ["python", "model.py"]
```

---

##  Build Docker Image

```bash
docker build -t tensorflow-model .
```

---

## ▶️ Run Container

```bash
docker run tensorflow-model
```

---

##  Expected Output

```text
Model loaded successfully
```

---

##  Key Concepts Demonstrated

* Containerizing machine learning models
* Using pre-built TensorFlow Docker images
* Creating portable ML environments
* Eliminating dependency conflicts

---

## Notes

* The TensorFlow image is large (~2GB+), so build time may be longer
* Internet connection is required initially to download model weights
* No GPU support is configured in this setup (CPU only)

---

## ‍ Author

Pawan Kumar Panchal

