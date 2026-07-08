# Práctica: WordPress con Docker, Git y Jenkins

Proyecto sencillo para desplegar WordPress con MySQL usando Docker Compose y realizar el redepliegue desde Jenkins.

## Archivos

- `docker-compose.yml`: define WordPress, MySQL, red y volúmenes.
- `.env`: contiene las variables del ambiente.
- `Jenkinsfile`: contiene el Pipeline.
- `evidencias/`: lugar para guardar las capturas.

## Requisitos

- Docker Engine
- Docker Compose
- Git
- Jenkins

## 1. Levantar el ambiente

Desde la carpeta del proyecto:

```bash
docker compose up -d
```

Verificar los contenedores:

```bash
docker ps
```

Verificar la red:

```bash
docker network ls
```

Verificar los volúmenes:

```bash
docker volume ls
```

## 2. Validar la comunicación

Revisar la red del contenedor de WordPress:

```bash
docker inspect wordpress_app
```

Revisar la red del contenedor de MySQL:

```bash
docker inspect wordpress_db
```

En ambos resultados debe aparecer la red `wordpress_network`.

También se puede usar:

```bash
docker inspect wordpress_app --format '{{json .NetworkSettings.Networks}}'
docker inspect wordpress_db --format '{{json .NetworkSettings.Networks}}'
```

## 3. Abrir WordPress

Ingresar en el navegador:

```text
http://localhost:8080
```

Debe aparecer el asistente inicial de instalación de WordPress.

## 4. Subir a GitHub

El proyecto ya contiene tres commits. Crear un repositorio vacío en GitHub y ejecutar:

```bash
git remote add origin URL_DEL_REPOSITORIO
git push -u origin main
```

Para revisar los commits:

```bash
git log --oneline
```

## 5. Configurar Jenkins

1. Crear un nuevo elemento de tipo `Pipeline`.
2. Elegir `Pipeline script from SCM`.
3. Seleccionar `Git`.
4. Colocar la dirección del repositorio.
5. Usar la rama `main`.
6. Dejar `Jenkinsfile` como ruta del script.
7. Guardar y ejecutar `Build Now`.

En Linux, Jenkins necesita permiso para usar Docker:

```bash
sudo usermod -aG docker jenkins
sudo systemctl restart jenkins
```

Después se puede ejecutar nuevamente el Pipeline.

## 6. Detener el ambiente

```bash
docker compose down
```

Para borrar también los volúmenes y empezar desde cero:

```bash
docker compose down -v
```

## Nota

Las contraseñas del archivo `.env` son únicamente para esta práctica local. No deben usarse en producción.
