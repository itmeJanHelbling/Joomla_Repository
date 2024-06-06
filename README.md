run Befehl für den MYSQL-Container
docker run -d --name joomla_db 
-e MYSQL_ROOT_PASSWORD=password 
-v joomla_db_data:/var/lib/mysql 
--network joomla_net 
-p 3306:3306 mysql:8.4

Bash für den MYSQL-Container öffnen
docker exec -it joomla_db bash

Mit dem MYSQL-Sever verbinden
mysql -u root -p




run Befehel für den Joomla-Container
docker run --name joomla_web 
--link joomla_db:mysql 
-e JOOMLA_DB_HOST=joomla_db 
-e JOOMLA_DB_USER=root 
-eJOOMLA_DB_PASSWORD=password 
-v joomla_data:/var/www/html 
--network joomla_net 
-p 8080:80 
-d joomla:5.1

