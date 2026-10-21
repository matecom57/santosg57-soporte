comandos esenciales
===================

Los comandos esenciales de Docker se dividen según su función principal para gestionar contenedores, imágenes y el entorno. Puedes consultar la guía detallada en 
Hostinger o revisar los conceptos básicos en DataCamp.

**Información del sistema y versión**

• ``docker --version``: Muestra la versión instalada de Docker.

• ``docker info``: Muestra información detallada del sistema y del demonio Docker.

• ``docker system df``: Muestra el espacio en disco que utilizan las imágenes, contenedores y volúmenes.


**Gestión de imágenes**

• ``docker pull <imagen>``: Descarga una imagen desde un registro (como Docker Hub).

• ``docker image ls`` (o ``docker images``): Lista todas las imágenes almacenadas localmente.

• ``docker build -t <nombre>`` .: Construye una imagen a partir de un archivo Dockerfile en el directorio actual.

• ``docker rmi <imagen>``: Elimina una imagen del sistema.


**Gestión de contenedores**

• ``docker run <imagen>``: Crea y ejecuta un nuevo contenedor a partir de una imagen.
• ``docker run -d -p <puerto_host>:<puerto_contenedor> <imagen>``: Ejecuta un contenedor en segundo plano (-d) mapeando puertos.
• ``docker ps``: Lista los contenedores que se encuentran en ejecución.
• ``docker ps -a``: Lista todos los contenedores (activos y detenidos).
• ``docker start <contenedor>``: Inicia un contenedor que ya está creado pero detenido.
• ``docker stop <contenedor>``: Detiene de forma segura un contenedor en ejecución.
• ``docker restart <contenedor>``: Reinicia un contenedor.
• ``docker rm <contenedor>``: Elimina un contenedor detenido.


**Interacción y diagnóstico**

• ``docker exec -it <contenedor> bash`` (o sh): Abre una terminal interactiva dentro de un contenedor en ejecución.
• ``docker logs <contenedor>``: Muestra los registros (logs) generados por el contenedor.
• ``docker inspect <contenedor>``: Muestra información de bajo nivel y configuración del contenedor.


**Redes y volúmenes**

• ``docker network ls``: Lista las redes de Docker disponibles.
• ``docker network create <nombre>``: Crea una nueva red.
• ``docker volume ls``: Lista los volúmenes para persistencia de datos.
• ``docker volume create <nombre>``: Crea un nuevo volumen.


**Docker Compose**

• ``docker compose up -d``: Inicia todos los servicios definidos en un archivo docker-compose.yml en segundo plano.
• ``docker compose down``: Detiene y elimina los contenedores y redes creados por docker compose up.



