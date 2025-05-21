# 🐋 Imágenes en Docker

## 🧱 ¿Qué son las imágenes?

Las imágenes en Docker son **plantillas inmutables** que contienen todo lo necesario para ejecutar una aplicación: código, librerías, variables, dependencias y configuraciones.

🐾 *Imagina que creas una réplica exacta de un dojo (templo de entrenamiento). Cada vez que la usas, puedes hacer que un nuevo gato ninja entrene allí sin tener que reconstruirlo todo.*

---

## 🖼️ Primera imagen: ¡tu "Hello World" Dockerizado!

```dockerfile
# Dockerfile
FROM alpine
CMD ["echo", "こんにちは世界 (Hola Mundo en japonés)"]
```

Construir la imagen:

```bash
docker build -t saludo_japones .
```

Ejecutarla:

```bash
docker run saludo_japones
```

---

## 📁 Copiando archivos al contenedor

Para incluir archivos en tu contenedor, usa `COPY` o `ADD`:

```dockerfile
FROM ubuntu
COPY script.sh /app/script.sh
```

Esto mueve `script.sh` de tu máquina al contenedor, a `/app/script.sh`.

---

## 🌿 Variables de entorno

Puedes definir variables con `ENV` en tu `Dockerfile`:

```dockerfile
FROM node
ENV PUEDO_MIAU "sí"
CMD ["node", "-e", "console.log(process.env.PUEDO_MIAU)"]
```

O al ejecutar:

```bash
docker run -e PUEDO_MIAU=no mi_contenedor
```

🐱 *Los ninjas a veces tienen técnicas secretas ocultas (variables) que activan poderes especiales.*

---

## 🔄 Ejecutar servicios

```dockerfile
FROM nginx
COPY index.html /usr/share/nginx/html
```

Esto permite iniciar un servicio web cuando se ejecute el contenedor:

```bash
docker run -d -p 8080:80 mi_nginx
```

---

## ⚔️ ENTRYPOINT vs CMD

| Comando      | Se usa para... | Se puede sobrescribir con argumentos `docker run` |
|--------------|----------------|-------------------|
| `CMD`        | Instrucción por defecto si no se pasa ninguna | ✅ Sí |
| `ENTRYPOINT` | Fijar el ejecutable principal del contenedor | 🚫 No (excepto con `--entrypoint`) |

🔧 Ejemplo combinado:

```dockerfile
FROM python
COPY app.py .
ENTRYPOINT ["python3"]
CMD ["app.py"]
```

Puedes sobrescribir `CMD` con otro archivo, pero `ENTRYPOINT` seguirá siendo `python3`.

---

## 🐍 Dockerizar un script Python

1. Archivo `app.py`:

```python
print("Hola desde un script ninja en Python 🐍")
```

2. `Dockerfile`:

```dockerfile
FROM python:3.9-slim
COPY app.py /app.py
CMD ["python", "/app.py"]
```

3. Build y run:

```bash
docker build -t python-neko .
docker run python-neko
```

---

## 🟢 Dockerizar un script Node.js

1. Archivo `app.js`:

```js
console.log("Hola desde un script ninja en Node.js 🟢");
```

2. `Dockerfile`:

```dockerfile
FROM node:20
COPY app.js /app.js
CMD ["node", "/app.js"]
```

3. Build y run:

```bash
docker build -t node-neko .
docker run node-neko
```

---

## ☁️ Publicar en Docker Hub

1. Inicia sesión:

```bash
docker login
```

2. Taggea tu imagen:

```bash
docker tag node-neko tu_usuario/node-neko
```

3. Súbela:

```bash
docker push tu_usuario/node-neko
```

🔗 Luego podrás ejecutar tu imagen desde cualquier parte del mundo:

```bash
docker run tu_usuario/node-neko
```

---

> 🧘‍♀️ *Al crear imágenes Docker, estás construyendo templos virtuales para tus scripts samuráis. Puedes replicarlos, moverlos o compartirlos... como pergaminos secretos del código.*

