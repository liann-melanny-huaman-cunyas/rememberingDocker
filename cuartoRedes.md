# 🐳 Docker + Portainer, Aplicaciones Gráficas y Entornos VSCode

Docker no solo sirve para aplicaciones backend o servidores, también puedes usarlo para gestionar contenedores gráficamente, correr apps con interfaces, y configurar tu entorno de desarrollo con Visual Studio Code.

---

## 🧭 Docker + Portainer: Gestión visual de contenedores

**Portainer** es una herramienta web para administrar contenedores Docker desde un navegador. Ideal si eres nuevo en Docker o prefieres algo visual.

### 🛠️ Instalación rápida

```bash
docker volume create portainer_data

docker run -d -p 9000:9443 -p 8000:8000 --name portainer \
  --restart=always \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v portainer_data:/data \
  portainer/portainer-ce:latest
```

Luego accede a: [https://localhost:9443](https://localhost:9443)

🐱 *Es como tener un tablero de control para tu aldea ninja. Todo lo gestionas desde un mismo lugar: contenedores, volúmenes, redes y más.*

---

## 🖥️ Docker para Aplicaciones Gráficas

Docker también permite correr **aplicaciones con GUI** (interfaz gráfica), como navegadores, editores de imagen, etc.

### 🧪 Ejemplo: Firefox en Docker (Linux)

```bash
docker run -e DISPLAY=$DISPLAY \
  -v /tmp/.X11-unix:/tmp/.X11-unix \
  jess/firefox
```

> 📝 Requiere tener servidor X y permitir acceso con: `xhost +local:docker`

🐾 *Como tener un pequeño templo ninja donde se ejecuta tu navegador, aislado del resto del sistema.*

---

## 💻 Docker + VSCode: Entornos de desarrollo

Con **Visual Studio Code** y su extensión **Dev Containers**, puedes crear un entorno de desarrollo dentro de un contenedor.

### 🔌 Requisitos

1. Instala [VSCode](https://code.visualstudio.com/)
2. Instala la extensión **Dev Containers**
3. Crea el archivo `.devcontainer/devcontainer.json`:

```json
{
  "name": "Neko Dev Env",
  "image": "node:20",
  "postCreateCommand": "npm install",
  "forwardPorts": [3000],
  "mounts": ["source=${localWorkspaceFolder}/data,target=/app/data,type=bind"]
}
```

4. Abre VSCode > `Ctrl+Shift+P` > `Dev Containers: Reopen in Container`

### 🧾 ¿Para qué sirve?

- Mismo entorno para todos los desarrolladores
- Aislamiento completo del host
- Ideal para proyectos con dependencias pesadas

🐱 *Tu VSCode se convierte en un dojo portátil: sin importar la máquina, entrenas siempre igual.*

---

## 📦 Extra: Ejecutar GUI desde Docker + VSCode

Puedes levantar un contenedor con entorno de escritorio completo (ej. XFCE o GNOME) usando imágenes como `dorowu/ubuntu-desktop-lxde-vnc`.

```bash
docker run -p 6080:80 dorowu/ubuntu-desktop-lxde-vnc
```

Luego accede a: `http://localhost:6080`

---

> 🎌 Docker no solo es para servidores. Con herramientas como Portainer, Dev Containers y apps gráficas, puedes crear tu propio templo digital para desarrollar, probar y administrar todo desde tu aldea de contenedores. 🐾🗾

