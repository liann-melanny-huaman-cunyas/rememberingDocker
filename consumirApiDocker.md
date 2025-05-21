# 🐳 Consumir APIs en Docker

Cuando tienes una aplicación dentro de un contenedor Docker, puede que necesites **consumir una API externa** (como una REST API pública) o incluso una API de otro contenedor dentro de tu red Docker.

---

## 🌐 1. Consumir una API Pública desde un Contenedor

Supongamos que tienes un script Python que consulta una API pública (como la de gatos 🐱):

### `main.py`
```python
import requests

response = requests.get('https://api.thecatapi.com/v1/images/search')
data = response.json()
print("Gatito aleatorio 🐱:", data[0]["url"])
```

### Dockerfile
```dockerfile
FROM python:3.10-slim

WORKDIR /app

COPY main.py .

RUN pip install requests

CMD ["python", "main.py"]
```

### Build y ejecución
```bash
docker build -t cat-api-app .
docker run cat-api-app
```

📡 *El contenedor actúa como un monje que consulta el clima en otra aldea conectada por red (la API pública).*

---

## 🔗 2. Consumir la API de Otro Contenedor (Red Interna)

Supongamos que tienes una **API Node.js** y un cliente que la consume.

### 📦 API (servidor Express)
**Archivo `api/index.js`**
```js
const express = require('express');
const app = express();

app.get('/neko', (req, res) => {
  res.json({ message: 'Hola desde la API de gatitos 😺' });
});

app.listen(3000, () => console.log('API corriendo en puerto 3000'));
```

### Dockerfile API
```dockerfile
FROM node:20

WORKDIR /api

COPY api/ .

RUN npm install express

EXPOSE 3000

CMD ["node", "index.js"]
```

---

### 📦 Cliente (Python)

**Archivo `client.py`**
```python
import requests

res = requests.get("http://api:3000/neko")
print(res.json())
```

### Dockerfile Cliente
```dockerfile
FROM python:3.10-slim

WORKDIR /client

COPY client.py .

RUN pip install requests

CMD ["python", "client.py"]
```

---

## 🧱 docker-compose.yml (red compartida)

```yaml
version: '3.8'

services:
  api:
    build:
      context: .
      dockerfile: Dockerfile.api
    container_name: api
    ports:
      - "3000:3000"

  client:
    build:
      context: .
      dockerfile: Dockerfile.client
    depends_on:
      - api
```

### Ejecutar
```bash
docker-compose up --build
```

> 🔁 *Ambos contenedores viven en la misma aldea ninja y pueden comunicarse por su nombre de servicio, como `http://api:3000/neko`.*

---

## 🔐 ¿Y si la API tiene tokens?

Puedes usar **variables de entorno** para pasar el token:

```bash
docker run -e API_TOKEN=abc123 cat-api-app
```

Y en tu código:

```python
import os
token = os.getenv("API_TOKEN")
headers = {"Authorization": f"Bearer {token}"}
requests.get("https://api.segura.com/data", headers=headers)
```

---

> 🧘‍♀️ Consumir APIs dentro de Docker es como enviar mensajeros entre aldeas. Ya sea pública o privada, asegúrate de conocer bien su camino (URL) y reglas de acceso (puertos o tokens). 🐱📨

