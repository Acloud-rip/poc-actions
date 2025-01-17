# Guía para Configurar y Desplegar tu Proyecto con Pulumi y Google Cloud

Este documento proporciona una guía paso a paso para configurar y desplegar un proyecto utilizando Pulumi, Python, y Google Cloud.

---

## **Pre-requisitos**

Asegúrate de tener los siguientes componentes instalados y configurados:

1. **Instalar Pulumi**
   - Consulta la [documentación oficial](https://www.pulumi.com/docs/iac/download-install/) para descargar e instalar Pulumi.

2. **Instalar Python**
   - Versión requerida: 3.7 o superior.

3. **Instalar el SDK de Google Cloud**
   ```bash
   curl https://sdk.cloud.google.com | bash && exec -l $SHELL && gcloud init
   ```

4. **Configurar el Stack de Pulumi**
   - Asegúrate de tener un stack en Pulumi con el mismo nombre del stack definido en este repositorio.

---

## **Pasos Iniciales Luego de Clonar el Repositorio**

1. **Autenticar tu cuenta en Google Cloud**
   ```bash
   gcloud auth application-default login
   ```

2. **Configurar entorno virtual de Python**
   - Si no tienes un entorno virtual configurado:
     ```bash
     python -m venv venv
     ```
   - Si ya tienes uno, actívalo:
     ```bash
     source venv/bin/activate
     ```

3. **Instalar dependencias**
   ```bash
   pip install -r requirements.txt
   ```

4. **Iniciar sesión en Pulumi**
   ```bash
   pulumi login
   ```

5. **Seleccionar el Stack de Pulumi**
   - Asegúrate de usar el mismo nombre del stack configurado en `pulumi.yaml`.
   ```bash
   pulumi stack select <USER>/NameProject/NameStack
   ```
   - Ejemplo:
     ```bash
     pulumi stack select LuisRiosAcloud/virtualmachinedev/dev
     ```

6. **Comandos para despliegue**
   - Probar la conexión con GCP y Pulumi:
     ```bash
     pulumi preview
     ```
   - Desplegar el proyecto:
     ```bash
     pulumi up
     ```
   - Destruir la infraestructura si es necesario:
     ```bash
     pulumi destroy
     ```

---

## **Configurar GitHub Actions**

Para interactuar con GitHub Actions en este repositorio, sigue estos pasos:

1. **Configurar credenciales de Pulumi en GitHub Secrets**
   - Ve a tu perfil de GitHub y extrae tu token de acceso de Pulumi.
   - Configura el secret con la siguiente estructura (reemplaza `<...>` con los valores correspondientes):
     ```
     <USERGITHUB>_PULUMI_ACCESS_TOKEN
     <USERGITHUB>_STACK_NAME
     ```

2. **Consideraciones al trabajar en nuevas ramas**
   - Asegúrate de que los secrets configurados sean accesibles para cualquier rama en la que trabajes.

---

¡Eso es todo! Ahora puedes trabajar en tu proyecto de manera eficiente y sin contratiempos. Si encuentras algún problema, no dudes en consultar la documentación oficial o buscar ayuda en la comunidad.
