# DevOps_PruebaTecnica – Ingeniero DevOps

Este repositorio contiene la solución a la prueba técnica para el cargo de **Ingeniero DevOps**.  
El objetivo del ejercicio fue implementar un flujo básico de **CI/CD** que incluya análisis de calidad de código, ejecución de pruebas, construcción de contenedores y validaciones de seguridad.


# 1. Descripción del proyecto

Se desarrolló una pequeña API utilizando **Python y FastAPI** con el fin de contar con una funcionalidad básica sobre la cual aplicar el pipeline de integración continua.

La API expone un endpoint simple que permite validar que el servicio se encuentra funcionando correctamente.

El enfoque principal del ejercicio no es la lógica de negocio sino la implementación de prácticas DevOps como:

- Integración continua
- Automatización de pruebas
- Análisis de calidad de código
- Seguridad en contenedores
- Flujo de despliegue por ambientes


# 2. Estructura del proyecto

El proyecto tiene la siguiente estructura:

DevOps_PruebaTecnica
│
├── app
│ └── main.py
│
├── tests
│ └── test_main.py
│
├── Dockerfile
├── requirements.txt
├── sonar-project.properties
└── .github/workflows/devops-pipeline.yml

Descripción de los componentes principales:

- **app/**: contiene la aplicación FastAPI.
- **tests/**: pruebas automatizadas ejecutadas con pytest.
- **Dockerfile**: permite construir la imagen del servicio.
- **requirements.txt**: dependencias del proyecto.
- **sonar-project.properties**: configuración para análisis de calidad con SonarCloud.
- **.github/workflows/**: definición del pipeline CI/CD.

# 3. Estrategia de ramas

Se implementó un flujo simple basado en ambientes:

- **dev** → desarrollo
- **qa** → ambiente de pruebas
- **main** → producción

Estas ramas fueron configuradas como **ramas protegidas**, lo que obliga a trabajar mediante **Pull Requests** antes de integrar cambios.

# 4. Pipeline CI/CD

Se implementó un pipeline utilizando **GitHub Actions**, el cual se ejecuta automáticamente al realizar cambios en las ramas protegidas.

El pipeline incluye las siguientes etapas:

### 1. Análisis de calidad de código

Se realiza análisis estático utilizando **SonarCloud** para evaluar:

- calidad del código
- mantenibilidad
- posibles vulnerabilidades

### 2. Ejecución de pruebas

Se ejecutan pruebas automatizadas con **pytest** para validar el funcionamiento básico de la aplicación.

### 3. Construcción del contenedor

Se construye una imagen **Docker** del servicio utilizando el Dockerfile definido en el proyecto.

### 4. Escaneo de seguridad

La imagen generada es analizada utilizando **Trivy**, con el fin de identificar posibles vulnerabilidades en el contenedor.

### 5. Despliegue por ambientes

Dependiendo de la rama en la que se ejecute el pipeline:

- cambios en **qa** ejecutan el paso de despliegue a ambiente de pruebas
- cambios en **main** ejecutan el paso de despliegue a producción

Para efectos de la prueba técnica, el despliegue se encuentra simulado mediante mensajes en el pipeline, dejando preparado el flujo para integrarse con un proveedor cloud como **AWS (ECR / ECS)**.

---
