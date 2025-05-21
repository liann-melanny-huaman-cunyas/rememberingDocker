# 🧠 ¿Qué es un Orquestador?

Un **orquestador** es una herramienta que se encarga de **gestionar y coordinar múltiples contenedores** automáticamente. Decide **cuándo, dónde y cómo** deben ejecutarse tus aplicaciones.

🐱 *Imagínate un templo donde cientos de gatos samuráis entrenan (contenedores). El orquestador es el gran sensei que decide qué gato entrena dónde, cuándo descansar o reubicarse si algo falla.*

---

# ⚙️ Conceptos Básicos

- **Nodo (Node)**: Es una máquina (real o virtual) donde se ejecutan los contenedores.
- **Pod**: Es la unidad mínima en Kubernetes, puede contener uno o varios contenedores.
- **Cluster**: Conjunto de nodos gestionados por un orquestador como Kubernetes.
- **Namespace**: Espacio lógico para agrupar recursos en un clúster.
- **Deployment**: Describe cómo y cuántas réplicas de un pod quieres.
- **Service**: Permite exponer un pod para recibir tráfico interno o externo.

---

# 🏗️ 3 Formas de Instalar Kubernetes (K8s)

1. **Minikube** (ideal para locales):
```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
minikube start
```

2. **Kind (Kubernetes in Docker)**:
```bash
go install sigs.k8s.io/kind@latest
kind create cluster
```

3. **K3s** (versión ligera para servidores):
```bash
curl -sfL https://get.k3s.io | sh -
```

---

# 🥷 Primer Pod

1. Crear archivo `pod.yaml`:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: neko-pod
spec:
  containers:
    - name: neko-container
      image: nginx
```

2. Aplicar:

```bash
kubectl apply -f pod.yaml
```

3. Ver pods:

```bash
kubectl get pods
```

🐾 *Como invocar a tu primer gato ninja para vigilar el templo.*

---

# 🌐 Port Forward: Acceder al Pod

Para exponer el puerto 80 del pod al puerto 8080 de tu máquina:

```bash
kubectl port-forward pod/neko-pod 8080:80
```

Luego accede a: [http://localhost:8080](http://localhost:8080)

---

# 💻 Terminal Interactiva en el Pod

Entra al contenedor:

```bash
kubectl exec -it neko-pod -- /bin/sh
```

Ahora puedes interactuar con el sistema del contenedor. Sal con `exit`.

---

# ❌ Eliminar Pods

Para borrar el pod:

```bash
kubectl delete pod neko-pod
```

---

# 📜 Ver Logs de un Pod

Si tu contenedor genera logs, puedes verlos con:

```bash
kubectl logs neko-pod
```

Si tiene varios contenedores:

```bash
kubectl logs neko-pod -c nombre_del_contenedor
```

---

> 🧘‍♀️ *Kubernetes es como un templo lleno de gatos entrenando artes místicas. Con el orquestador como sensei, todo se equilibra y se ejecuta a la perfección, incluso cuando uno de ellos necesita ser reemplazado o descansar.* 🐱🌸

