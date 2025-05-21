# 🐳 Curso Profesional de Docker

¡Bienvenido al mundo de **Docker**! En esta guía descubrirás los conceptos esenciales para dominar esta herramienta, con ejemplos inspirados en la cultura japonesa 🇯🇵 y nuestros adorables amigos felinos 🐾.

---

## 🛠️ Dockerfile

Un `Dockerfile` es como una **receta** para preparar tu contenedor. Describe **paso a paso** cómo construir una imagen, al igual que una receta de **ramen japonés** que indica qué ingredientes usar y cómo cocinarlos.

### Ejemplo:
```Dockerfile
FROM node:20-alpine
WORKDIR /app
COPY . .
RUN npm install
CMD ["npm", "start"]
```

📦 **Analógico japonés:** Imagina que estás creando una *bento box* 🥢. El `Dockerfile` te dice cómo preparar el arroz, cortar el sushi y acomodar todo en la caja. 🥡

---

## 🖼️ Imagen (Image)

Una **imagen Docker** es el resultado de construir un `Dockerfile`. Es como una **katana terminada**, lista para usarse, forjada con precisión a partir de instrucciones.

🔁 Es **inmutable**: no cambia una vez creada. Si quieres una nueva versión, debes construir otra.

📦 **Ejemplo gatuno:** Una imagen podría ser como un retrato digital de tu gato favorito vestido de samurái. Siempre será igual cada vez que lo abras 🐱⚔️.

---

## 📦 Contenedor (Container)

Un **contenedor** es una **instancia en ejecución** de una imagen. Es como invocar un **espíritu de batalla** desde una carta de invocación en un anime — se crea temporalmente, hace su trabajo, y luego puede desaparecer.

🧳 Piensa en un **gato ninja** que aparece, cumple su misión, y se esfuma sin dejar rastro.

```bash
docker run -d -p 3000:3000 myapp
```

---

## ☁️ Docker Hub

[**Docker Hub**](https://hub.docker.com) es como el **mercado digital de contenedores**. Allí puedes:

- Subir tus imágenes (como si fueran obras de arte)
- Descargar imágenes de otros (como si compraras ramen instantáneo de diferentes partes de Japón)

🎏 **Ejemplo cultural:** Es como visitar **Akihabara**, pero en vez de figuras de anime, encuentras imágenes listas para usar en tus servidores.

```bash
docker pull nginx
docker push username/myapp
```

---

## ⚙️ Docker Daemon

El **Docker Daemon** (`dockerd`) es el **cerebro maestro** detrás de todo. Es un proceso que escucha tus órdenes (`docker build`, `docker run`) y las ejecuta.

👘 **Ejemplo japonés:** Imagina que el Daemon es como el **sensei** de un dojo de gatos ninjas 🐈‍⬛. Tú das la orden, y él entrena y lanza a los contenedores al campo de batalla.

---

## 🧠 Conclusión

Docker te permite:

- Empaquetar tus aplicaciones como si fueran *bentos listos para llevar*
- Compartirlas como si fueran mangas en una feria de tecnología
- Ejecutarlas como si tuvieras un **ejército de gatitos automatizados** haciendo tareas por ti 🐾

---

> "Así como los samuráis confiaban en sus espadas, los DevOps confían en sus contenedores." 🥷🐳
