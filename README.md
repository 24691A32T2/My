# Check Docker version 17 week
docker --version

# Create Docker network
docker network create mynetwork

# Run MySQL container
docker run --name mysql-container \
--network mynetwork \
-e MYSQL_ROOT_PASSWORD=root \
-e MYSQL_DATABASE=mydb \
-d mysql:latest

# Run phpMyAdmin container
docker run --name phpmyadmin-container \
--network mynetwork \
-d -e PMA_HOST=mysql-container \
-p 8080:80 phpmyadmin/phpmyadmin
