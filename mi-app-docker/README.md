
# Comandos básicos gestión Docker
## Ver contenedores en ejecución
docker ps

## Ver todos los contenedores (incluyendo detenidos)
docker ps -a

## Ver imágenes descargadas
docker images

## Detener un contenedor
docker stop mi-nginx

## Eliminar un contenedor
docker rm mi-nginx

## Eliminar una imagen
docker rmi nginx

## Ver logs de un contenedor
docker logs mi-nginx

## Entrar a la terminal de un contenedor en ejecución
docker exec -it mi-nginx bash

# Construcción
docker build -t nombre:tag .            # Construir imagen
docker build --no-cache -t nombre:tag . # Construir sin caché

# Ejecución
docker run -d -p host:contenedor --name nombre imagen  # Ejecutar en background
docker run -it imagen bash              # Ejecutar interactivo con terminal

# Gestión de contenedores
docker ps                  # Contenedores en ejecución
docker ps -a               # Todos los contenedores
docker stop nombre         # Detener
docker start nombre        # Iniciar detenido
docker rm nombre           # Eliminar (debe estar detenido)
docker rm -f nombre        # Eliminar forzando detención

# Gestión de imágenes
docker images              # Listar imágenes
docker rmi nombre:tag      # Eliminar imagen
docker pull imagen:tag     # Descargar imagen sin ejecutar

# Inspección y logs
docker logs nombre         # Ver logs
docker logs -f nombre      # Logs en tiempo real
docker exec -it nombre sh  # Abrir shell en contenedor activo
docker inspect nombre      # Información detallada en JSON

# Limpieza
docker system prune        # Eliminar todo lo no usado (pide confirmación)
docker system prune -a     # Incluye imágenes no referenciadas

# Docker Compose
docker compose up -d             # Levantar todos los servicios
docker compose up -d --build     # Levantar reconstruyendo imágenes
docker compose down              # Bajar y eliminar contenedores y red
docker compose ps                # Ver estado de los servicios
docker compose logs -f           # Logs en tiempo real de todos
docker compose logs -f servicio  # Logs de un servicio específico
docker compose exec web sh       # Shell en el servicio 'web'
docker compose restart web       # Reiniciar un servicio
docker compose stop              # Detener sin eliminar
docker compose start             # Iniciar servicios detenidos