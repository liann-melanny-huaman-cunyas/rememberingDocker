## 📦 Volúmenes en Docker

Los volúmenes son la forma que tiene Docker de **gestionar datos persistentes** fuera del ciclo de vida del contenedor. Al usarlos, puedes guardar información incluso después de que el contenedor sea eliminado.

🐾 *Piensa en ellos como una biblioteca secreta del templo donde tus gatos samuráis almacenan conocimientos sagrados, sin importar cuántas veces entrenen o cambien de dojo (contenedor).*

---

### 🧩 ¿Qué son los volúmenes?

Los volúmenes son **directorios gestionados por Docker** que puedes montar dentro de los contenedores para:

- Almacenar datos de manera persistente 🧠
- Compartir archivos entre contenedores 🤝
- Mantener separados los datos del entorno de ejecución 🚀

---

## 🎏 Volúmenes de Docker

Puedes crear volúmenes usando el siguiente comando:

```bash
docker volume create mi_volumen
```

Y luego usarlo al ejecutar un contenedor:

```bash
docker run -d -v mi_volumen:/usr/share/nginx/html nginx
```

📁 *Esto monta el volumen `mi_volumen` en la ruta interna `/usr/share/nginx/html` del contenedor.*

---

### 🐱 Compartir archivos entre contenedores

Imagina dos gatos que quieren compartir un pergamino secreto.

```bash
docker run -d --name cont1 -v gato_vol:/datos ubuntu sleep 9999
docker run -it --name cont2 --volumes-from cont1 ubuntu
```

💬 Ambos contenedores comparten el volumen `gato_vol`. Todo lo que el primero escriba en `/datos`, el segundo podrá leerlo.

---

### 🧙‍♂️ Volúmenes manuales (bind mounts)

También puedes usar rutas de tu máquina (host) directamente:

```bash
docker run -v /ruta/en/host:/app ubuntu
```

🗂️ *Esto se llama “bind mount” y permite usar carpetas locales directamente en el contenedor.*

⚠️ Ideal para desarrollo, pero menos seguro en producción.

---

### 🔍 Ver todos los volúmenes

```bash
docker volume ls
```

### 🧹 Eliminar un volumen

```bash
docker volume rm mi_volumen
```

### 💣 Eliminar todos los volúmenes no usados

```bash
docker volume prune
```

---

## 🌸 Ejemplo completo

1. Crear un volumen:
   ```bash
   docker volume create datos_gato
   ```

2. Crear un contenedor que escriba datos:
   ```bash
   docker run -it --name gato1 -v datos_gato:/info ubuntu bash
   echo "Neko fue aquí" > /info/mensaje.txt
   ```

3. Otro contenedor leyendo los datos:
   ```bash
   docker run -it --name gato2 -v datos_gato:/info ubuntu cat /info/mensaje.txt
   ```

📜 *Ambos contenedores comparten el conocimiento del volumen, como un antiguo manuscrito de artes ninja.*

---

> 🧘‍♂️ *Sensei dockeriano: dominar los volúmenes te permite separar lo efímero (contenedores) de lo eterno (datos).*

