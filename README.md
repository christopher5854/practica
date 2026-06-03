# practica
docker pull mysql:9
docker images
docker run --name mysql_clase -d -p 3399:3306 mysql:9
docker ps -a
docker logs mysql_clase
docker rm mysql_clase
docker ps -a
docker run --name mysql_clase -d -p 3399:3306 -e MYSQL_ROOT_PASSWORD=12345 -e MYSQL_DATABASE=bd_clase  mysql:9
docker ps
docker exec -it mysql_clase bash
bash-5.1# ls
bash-5.1# mysql -u root -p
Enter password:12345
show databases;
ELIMINAR CONTENDEOR
docker stop mysql_clase
docker rm mysql_clase 
docker ps
docker ps -a
docker rm mysql_clase
docker network ls
docker network create red_clase 
docker network ls 
docker run --name mysql_prectica -d -p 3399:3306 -e MYSQL_ROOT_PASSWORD=12345 --network red_clase mysql:9
docker ps -q
docker ps -a 
docker network inspect red_clase 
docker run --name phpmyadmin_clase -d -p 8080:80 -e PMA_HOST=mysql_practica --network red_clase phpmyadmin
docker ps -a
docker exec -it mysql_practica bash
mysql -u root -p
mysql> show databases;
