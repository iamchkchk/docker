# docker

docker run --name env71 --link mysql57:mysql --link redis40:redis -it -d -p 80:80 -v /c/wamp/www:/var/www/html -v /c/Users/1111003/dockerbase/apache2:/var/log/apache2 dev/apachephp71:latest  

docker run --name env56 --link mysql57:mysql --link redis40:redis -it -d -p 80:80 -v /c/wamp/www:/var/www/html -v /c/Users/1111003/dockerbase/apache2:/var/log/apache2 dev/apachephp56:latest  


docker run --name mysql57 -v /d/dockerbase/mysql/data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=root -d mysql  

docker run -it --link mysql57:mysql --rm mysql sh -c 'exec mysql -h"$MYSQL_PORT_3306_TCP_ADDR" -P"$MYSQL_PORT_3306_TCP_PORT" -uroot -p'  


docker run --name redis -p 6379:6379 -d redis40  

docker run -it --link redis40:redis --rm redis redis-cli -h redis -p 6379  


docker pull mysql  
docker pull elasticsearch  
docker pull redis  
docker pull kibana  

# /apache2-php71-ssl
docker build -t dev/httpd71ss .

# /apache2-php72-ssl
docker build -t dev/httpd72ss .  

# apache2.4 + ssl + php7.1 + mysql5.7 + redis
docker-compose -f myweb.yml down  
docker-compose -f myweb.yml up -d  

# apache2.4 + ssl + php7.2 + mysql5.7 + redis
docker-compose -f myweb72.yml down  
docker-compose -f myweb72.yml up -d  

# apache2.4 + ssl + php7.2 + mysql8 + redis
docker-compose -f myweb72-m8.yml down  
docker-compose -f myweb72-m8.yml up -d  

# gist
https://gist.github.com/iamchkchk/492cffb52cf269ed50fa39236e91d688  
https://gist.github.com/iamchkchk/a28340b24515f1e34ecc590a7b8d98e6  
https://gist.github.com/iamchkchk/082d9151e77a132585e6223117b34add  


# mysql 5.7
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'root';  
FLUSH PRIVILEGES;  

# NOTE : mysql5.7
docker run --name some-mysql -e MYSQL_ROOT_PASSWORD=root -d mysql:5.7

docker run --name some-mysql -p 3306:3306 -v /d/dockerbase/mysql/data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=root -d mysql:5.7 --innodb-use-native-aio=0

docker exec -it some-mysql bash

mysql -uroot -proot

GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'root';  
FLUSH PRIVILEGES;  

docker stop some-mysql

docker rm some-mysql

# mysql 8
ALTER USER 'root'@'%' IDENTIFIED WITH mysql_native_password BY 'root';  
FLUSH PRIVILEGES;  

# NOTE : mysql8
docker run --name mysql8 -p 3306:3306 -v /d/dockerbase/mysql8/data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=root -d mysql --innodb-use-native-aio=0

docker exec -it mysql8 bash

mysql -uroot -proot

ALTER USER 'root'@'%' IDENTIFIED WITH mysql_native_password BY 'root';
FLUSH PRIVILEGES;

docker stop mysql8

docker rm mysql8