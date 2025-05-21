## 🐋 Gestión de Contenedores Docker

Explora cómo manipular contenedores como un verdadero sensei 🥷. Desde ejecutarlos en silencio como ninjas en segundo plano, hasta inspeccionarlos como un monje sabio. Todo con toques de la cultura japonesa y gatitos samuráis 🐾.

---

### 🎭 Contenedores en segundo plano (modo *detached*)

Ejecuta tu contenedor en segundo plano con `-d`.

```bash
docker run -d --name myapp nginx
```

🕶️ *Como un gato ninja que trabaja sin ser visto, silencioso y eficiente.*

---

### 💬 Modo interactivo

Usa `-it` para entrar al contenedor como si estuvieras dentro del dojo.

```bash
docker run -it ubuntu bash
```

📦 *Ideal para sesiones de entrenamiento en vivo dentro del contenedor, como conversar con un gato samurái.*

---

### 🌐 Exposición de puertos

Con `-p` mapeas los puertos de tu máquina local al contenedor.

```bash
docker run -d -p 8080:80 nginx
```

🚪 *Abres una puerta entre tu mundo y el mundo interior del contenedor, como el portal de un templo japonés.*

---

### 📜 Ver logs de un contenedor

Consulta los registros de actividad con:

```bash
docker logs myapp
```

📖 *Como leer el diario secreto de un gato ninja después de una misión encubierta.*

---

### 🔍 Inspeccionar contenedores

Obtén detalles técnicos de un contenedor con `inspect`.

```bash
docker inspect myapp
```

🧠 *Como analizar el ADN de un samurái felino para comprender su esencia y entrenamiento.*

---

### 🌱 Variables de entorno

Puedes pasar variables al contenedor con `-e`.

```bash
docker run -e NOMBRE_GATO=Shiro ubuntu env
```

🪷 *Como enseñar a tu gato a responder a su nombre en plena batalla.*

---

### 🧘‍♂️ Contenedores sin servicios

Puedes crear contenedores que no ejecuten servicios permanentes, útiles para pruebas.

```bash
docker run --name test-gato ubuntu echo "Konbanwa Neko-san"
```

⚙️ *Como invocar a tu gato solo para que diga una frase y luego desaparezca con una nube de humo.*

---

> 🧩 *Cada comando de Docker es como un kata en el arte del desarrollo moderno. Con práctica, dominarás el flujo y equilibrio entre código y contenedor.*

