### 🧩 Comandos básicos en Docker

Aquí tienes una lista de los comandos esenciales para comenzar a trabajar con Docker. Cada uno está acompañado de una analogía inspirada en la cultura japonesa y los gatos ninja 🐾🥷 para hacerlo más divertido y fácil de recordar.

---

#### 🐱 `docker --version`

Muestra la versión instalada de Docker.

```bash
docker --version
```

🎌 *Como preguntar al sensei qué grado de cinturón negro tiene en el arte del contenedor.*

---

#### 🐾 `docker pull`

Descarga una imagen desde Docker Hub o algún repositorio.

```bash
docker pull nginx
```

🎏 *Como traer ramen instantáneo importado desde Akihabara para cocinarlo localmente.*

---

#### 🐱 `docker build`

Construye una imagen a partir de un `Dockerfile`.

```bash
docker build -t myapp .
```

🍱 *Como preparar una bento box desde cero siguiendo la receta del `Dockerfile`.*

---

#### 🐾 `docker run`

Ejecuta un contenedor desde una imagen.

```bash
docker run -d -p 3000:3000 myapp
```

🥷 *Como lanzar a tu gato ninja entrenado al campo de batalla, listo para ejecutar su misión.*

---

#### 🐱 `docker ps`

Lista los contenedores que están ejecutándose.

```bash
docker ps
```

👀 *Como ver a tus pequeños gatitos samuráis trabajando en sus misiones secretas.*

---

#### 🐾 `docker stop`

Detiene un contenedor en ejecución.

```bash
docker stop <container_id>
```

🛏️ *Como decirle a tu gato ninja: "descansa, misión cumplida".*

---

#### 🐱 `docker rm`

Elimina un contenedor detenido.

```bash
docker rm <container_id>
```

🧹 *Como limpiar la arena del dojo luego de un entrenamiento.*

---

#### 🐾 `docker rmi`

Elimina una imagen de tu sistema local.

```bash
docker rmi myapp
```

📦 *Como deshacerte de una katana vieja que ya no necesitas.*

---

#### 🐱 `docker exec`

Ejecuta un comando dentro de un contenedor que ya está en ejecución.

```bash
docker exec -it myapp-container bash
```

🔍 *Como entrar al templo secreto donde entrenan tus gatos shinobi y dar órdenes desde dentro.*

---

#### 🐾 `docker logs`

Muestra los registros (logs) de un contenedor.

```bash
docker logs myapp-container
```

📜 *Como leer los pergaminos sagrados donde quedaron escritas las acciones del guerrero felino.*

---

> 🧘‍♀️ *Recuerda joven sensei del contenedor: cada comando es una técnica, y con práctica lograrás la armonía entre tu código y la infraestructura.*

