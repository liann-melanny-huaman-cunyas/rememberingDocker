# 🧩 Docker Compose: Orquestación de Contenedores

Docker Compose es una herramienta que permite **definir y ejecutar múltiples contenedores Docker** usando un solo archivo YAML (`docker-compose.yml`). Ideal para cuando tienes una aplicación compuesta por varios servicios (como una base de datos y un backend).

🐾 *Imagina un dojo donde cada sala tiene una función: una para entrenar, otra para meditar, otra para comer. Docker Compose te permite levantar todo el dojo con una sola orden.* 🏯

---

## 🧱 ¿Qué es un Servicio?

Un **servicio** es una definición de cómo se ejecutará un contenedor específico. Por ejemplo, un servicio `web` puede usar una imagen de NGINX, y un servicio `db` puede usar MySQL.

```yaml
services:
  web:
    image: nginx
  db:
    image: mysql
```

---

## 🔗 Redes en Docker Compose

Docker Compose crea automáticamente una red para que todos los servicios puedan comunicarse por nombre.

```yaml
services:
  app:
    image: node
    depends_on:
      - db
  db:
    image: mysql
```

En este caso, `app` puede conectarse a `db` con solo usar su nombre `db`.

---

## 📦 Volúmenes

Los volúmenes permiten **persistencia de datos** y compartir archivos entre servicios.

```yaml
services:
  db:
    image: mysql
    volumes:
      - db_data:/var/lib/mysql

volumes:
  db_data:
```

🐱 *Como el cuaderno de entrenamiento de un ninja: aunque el dojo se destruya, los aprendizajes (datos) persisten gracias al volumen.*

---

## 🌿 Variables de Entorno

Puedes usar `.env` o definir variables directamente:

**`.env`**:

```
MYSQL_ROOT_PASSWORD=neko123
```

**`docker-compose.yml`**:

```yaml
services:
  db:
    image: mysql
    environment:
      - MYSQL_ROOT_PASSWORD=${MYSQL_ROOT_PASSWORD}
```

---

## 🗂️ Stack local (modo desarrollo)

Puedes crear una pila completa local con `docker compose up`:

```bash
docker compose up
```

Para bajarla:

```bash
docker compose down
```

Para ver los logs:

```bash
docker compose logs -f
```

Para reiniciar un servicio:

```bash
docker compose restart nombre_servicio
```

🐾 *Como si un sensei dijera: “¡Todos a entrenar!” y todos los gatos entraran en acción según sus roles.*

---

## 🔨 docker compose build

Cuando trabajas con `Dockerfile` personalizados, puedes construirlos con:

```bash
docker compose build
```

Ejemplo:

```yaml
services:
  app:
    build:
      context: .
      dockerfile: Dockerfile
    ports:
      - "3000:3000"
```

---

## 🧪 Ejemplo Completo: Stack Ninja

**`docker-compose.yml`**:

```yaml
version: '3.8'

services:
  web:
    image: nginx
    ports:
      - "8080:80"
    volumes:
      - ./html:/usr/share/nginx/html

  app:
    build:
      context: .
      dockerfile: Dockerfile
    environment:
      - APP_MODE=desarrollo
    depends_on:
      - db

  db:
    image: mysql:8
    environment:
      - MYSQL_ROOT_PASSWORD=katana123
    volumes:
      - datos_mysql:/var/lib/mysql

volumes:
  datos_mysql:
```

---

> 🎌 *Docker Compose es como el pergamino del sensei: contiene las instrucciones para que todos los gatos samuráis del sistema trabajen en armonía.* 🐱⚔️

