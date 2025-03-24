# Docker Compose para Portainer

Este proyecto contiene un archivo `docker-compose.yml` que facilita la implementación de Portainer, una herramienta de administración de contenedores Docker basada en una interfaz web.

## ¿Qué es Portainer?

Portainer es una interfaz gráfica para Docker que permite gestionar contenedores, imágenes, redes, volúmenes y más de manera sencilla. Es muy útil para aquellos que prefieren trabajar con una interfaz visual en lugar de la línea de comandos.

## ¿Qué hace este `docker-compose.yml`?

Este archivo configura y despliega un contenedor de Docker que ejecuta Portainer. Los principales parámetros que se configuran son:

- **Imagen de Docker**: Utiliza la última versión estable de la imagen `portainer/portainer-ce` (Community Edition) desde Docker Hub.
- **Puertos**: El puerto 9000 de la máquina anfitriona se mapea al puerto 9000 del contenedor para que puedas acceder a la interfaz web de Portainer a través de `http://localhost:9000`.
- **Volúmenes**:
  - `/var/run/docker.sock:/var/run/docker.sock`: Permite que el contenedor de Portainer interactúe con el demonio Docker en la máquina anfitriona.
  - `portainer_data:/data`: Configura un volumen persistente para almacenar los datos y la configuración de Portainer.
- **Reinicio automático**: El contenedor se reinicia automáticamente si se detiene o si el sistema se reinicia, gracias a la opción `restart: always`.

## Requisitos

- Docker y Docker Compose deben estar instalados en tu máquina.

## ¿Cómo usarlo?

1. Clona este repositorio o copia el archivo `docker-compose.yml` a tu máquina.
2. Navega al directorio donde guardaste el archivo `docker-compose.yml`.
3. Ejecuta el siguiente comando en la terminal:

   ```bash
   docker-compose up -d
   ```

````

Este comando descargará la imagen de Portainer (si aún no está disponible en tu máquina) y pondrá en marcha el contenedor en segundo plano.

4. Abre tu navegador web y ve a `http://localhost:9000`. Podrás acceder a la interfaz de administración de Portainer.

## ¿Cómo detener y eliminar el contenedor?

Para detener el contenedor de Portainer, puedes ejecutar:

```bash
docker-compose down
```

Esto detendrá y eliminará el contenedor y la red asociada, pero conservará los volúmenes de datos.

## Contribuciones

Las contribuciones son bienvenidas. Si encuentras algún problema o deseas sugerir una mejora, no dudes en abrir un **Issue** o enviar un **Pull Request**.

## Licencia

Este proyecto está bajo la Licencia MIT - ver el archivo [LICENSE](LICENSE) para más detalles.
````

kubectl apply -f k8s/configmaps/kubeconfig-configmap.yaml
kubectl apply -f k8s/deployments/backend-deployment.yaml
kubectl apply -f k8s/services/backend-service.yaml

kubectl apply -f k8s/persistent-volumes/portainer-pvc.yaml
kubectl apply -f k8s/deployments/portainer-deployment.yaml
kubectl apply -f k8s/services/portainer-service.yaml

kubectl apply -f k8s/deployments/clusterrole.yaml
kubectl apply -f k8s/deployments/clusterrolebinding.yaml

kubectl apply -f k8s/deployments/postgres-deployment.yaml
kubectl apply -f k8s/deployments/auth-deployment.yaml
kubectl apply -f k8s/deployments/user-deployment.yaml

kubectl apply -f k8s/deployments/pgadmin-deployment.yaml
kubectl apply -f k8s/deployments/traefik-deployment.yaml
