# 🐳 Contenedor de herramientas DevOps: AWS CLI, kubectl, Terraform, Terragrunt y Docker CLI
Este proyecto crea un entorno Docker listo para usar con las principales herramientas de infraestructura como código y gestión en la nube.  
El contenedor se basa en **Ubuntu 24.04** e incluye **AWS CLI**, **kubectl**, **Terraform**, **Terragrunt** y **Docker CLI**, facilitando la automatización y despliegue de infraestructura desde un solo entorno.

---

## **📦 Herramientas instaladas**

### **1. AWS CLI**
- **Descripción:** La **AWS Command Line Interface (CLI)** permite gestionar los servicios de AWS mediante comandos en terminal, facilitando la automatización de tareas.  
- **Instalación en el contenedor:** Descargada directamente desde el instalador oficial de AWS y configurada en `/usr/local/bin/aws`.  
- **Enlace oficial:** [Instalación de AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)  
- **Binario usado:** [https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip](https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip)

---

### **2. kubectl**
- **Descripción:** Herramienta oficial de Kubernetes para desplegar, inspeccionar y gestionar recursos dentro de un clúster.  
- **Instalación en el contenedor:** Descargada desde la fuente oficial de Kubernetes con el comando `curl -LO`.  
- **Enlace oficial:** [Instalación de kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)  
- **Binario usado:** [https://dl.k8s.io/release/stable.txt](https://dl.k8s.io/release/stable.txt)

---

### **3. Terraform**
- **Descripción:** Herramienta de **HashiCorp** para construir, cambiar y versionar infraestructura de manera segura y eficiente.  
- **Instalación en el contenedor:** Añadido el repositorio oficial de HashiCorp y instalado mediante `apt install`.  
- **Enlace oficial:** [Instalación de Terraform](https://learn.hashicorp.com/tutorials/terraform/install-cli)  
- **Repositorio usado:** [https://apt.releases.hashicorp.com](https://apt.releases.hashicorp.com)

---

### **4. Terragrunt**
- **Descripción:** Wrapper para Terraform que facilita la gestión de múltiples entornos y configuraciones DRY (Don’t Repeat Yourself).  
- **Instalación en el contenedor:** Descargado desde GitHub, versión **v0.91.2**, y agregado a `/usr/local/bin/terragrunt`.  
- **Enlace oficial:** [Instalación de Terragrunt](https://terragrunt.gruntwork.io/docs/getting-started/install/)  
- **Binario usado:** [https://github.com/gruntwork-io/terragrunt/releases/download/v0.91.2/terragrunt_linux_amd64](https://github.com/gruntwork-io/terragrunt/releases/download/v0.91.2/terragrunt_linux_amd64)

---

### **5. Docker CLI**
- **Descripción:** El **cliente de Docker (Docker CLI)** permite interactuar con el daemon de Docker desde la línea de comandos, ejecutar `docker login`, construir imágenes, y administrar contenedores de forma remota o a través del socket del host.  
- **Instalación en el contenedor:** Se configura el repositorio oficial de Docker en Ubuntu y se instala el paquete `docker-ce-cli` mediante `apt install -y`.  
- **Enlace oficial:** [Instalación de Docker CLI](https://docs.docker.com/engine/install/ubuntu/)  
- **Paquete usado:** `docker-ce-cli`

---

## **⚙️ Estructura del proyecto**
```
├── Dockerfile                # Define las herramientas instaladas, incluyendo Docker CLI
├── Dockerfile-arm64          # Define las herramientas instaladas (arquitectura arm64)
├── docker-compose.yml        # Configura y levanta el contenedor
└── workspace/                # Directorio compartido con el contenedor
```

---

## **🚀 Instrucciones de uso**

### **1. Crear directorio de trabajo**
```bash
mkdir workspace
```

### **2. Levantar el contenedor**
Ejecuta el siguiente comando para construir la imagen y levantar el contenedor en segundo plano:
```bash
docker compose up -d
```

### **3. Acceder al contenedor**
Entra al contenedor con una terminal interactiva:
```bash
docker exec -it cloudops-cli bash
```

### **4. Verifica las herramientas instaladas**
```bash
aws --version
kubectl version --client
terraform version
terragrunt --version
docker --version
```
Si los comandos anteriores devuelven las versiones, el entorno está correctamente configurado.

---

## **🧰 Requisitos previos**
### **1. Instalación de Docker**
Para instalar Docker en tu sistema:
- **Enlace oficial:** [Guía de instalación de Docker](https://docs.docker.com/engine/install/)

---

## **🧾 Notas**
- El contenedor se mantiene activo con `stdin_open: true` y `tty: true`.  
- El directorio local `workspace/` se monta dentro del contenedor para compartir archivos y configuraciones.  
- Todo el entorno se basa en **Ubuntu 24.04 LTS**, con librerías esenciales como `curl`, `wget`, `vim`, `gpg` y **Docker CLI** instaladas.  
