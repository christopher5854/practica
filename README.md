# Práctica Docker MySQL

## 1. Descargar la imagen de MySQL

```bash
docker pull mysql:9
```

## 2. Verificar las imágenes descargadas

```bash
docker images
```

## 3. Crear un contenedor MySQL

```bash
docker run --name mysql_clase -d -p 3399:3306 mysql:9
```

## 4. Verificar contenedores

```bash
docker ps -a
```

## 5. Revisar los logs

```bash
docker logs mysql_clase
```

## 6. Eliminar el contenedor

```bash
docker rm mysql_clase
```

## 7. Verificar nuevamente

```bash
docker ps -a
```

## 8. Crear el contenedor con contraseña y base de datos

```bash
docker run --name mysql_clase -d -p 3399:3306 \
-e MYSQL_ROOT_PASSWORD=12345 \
-e MYSQL_DATABASE=bd_clase \
mysql:9
```

## 9. Verificar que esté ejecutándose

```bash
docker ps
```

## 10. Entrar al contenedor

```bash
docker exec -it mysql_clase bash
```

## 11. Listar archivos

```bash
ls
```

## 12. Entrar a MySQL

```bash
mysql -u root -p
```

Contraseña:

```text
12345
```

## 13. Mostrar bases de datos

```sql
show databases;
```

# Eliminar contenedor

## 14. Detener contenedor

```bash
docker stop mysql_clase
```

## 15. Eliminar contenedor

```bash
docker rm mysql_clase
```

## 16. Verificar contenedores activos

```bash
docker ps
```

## 17. Verificar todos los contenedores

```bash
docker ps -a
```

# Redes Docker

## 18. Ver redes

```bash
docker network ls
```

## 19. Crear red

```bash
docker network create red_clase
```

## 20. Verificar red creada

```bash
docker network ls
```

## 21. Crear MySQL dentro de la red

```bash
docker run --name mysql_practica -d \
-p 3399:3306 \
-e MYSQL_ROOT_PASSWORD=12345 \
--network red_clase \
mysql:9
```

## 22. Mostrar ID de contenedores

```bash
docker ps -q
```

## 23. Mostrar todos los contenedores

```bash
docker ps -a
```

## 24. Inspeccionar la red

```bash
docker network inspect red_clase
```

# phpMyAdmin

## 25. Crear contenedor phpMyAdmin

```bash
docker run --name phpmyadmin_clase -d \
-p 8080:80 \
-e PMA_HOST=mysql_practica \
--network red_clase \
phpmyadmin
```

## 26. Verificar contenedores

```bash
docker ps -a
```

## 27. Entrar al contenedor MySQL

```bash
docker exec -it mysql_practica bash
```

## 28. Iniciar sesión en MySQL

```bash
mysql -u root -p
```

Contraseña:

```text
12345
```

## 29. Mostrar bases de datos

```sql
show databases;
```

# Acceso a phpMyAdmin

Abrir en el navegador:

```text
http://localhost:8080
```

Usuario:

```text
root
```

Contraseña:

```text
12345
```
