# Laboratorio de despliegue automatizado

Proyecto de WordPress y MySQL desplegado con Docker Compose y automatizado mediante Jenkins.

## Archivos

- `docker-compose.yml`: configuración de WordPress y MySQL.
- `.env`: variables del ambiente.
- `Jenkinsfile`: Pipeline de despliegue.
- `README.md`: instrucciones del proyecto.

## Levantar el ambiente

```bash
docker compose up -d