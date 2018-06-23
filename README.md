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


docker build -t dev/httpd71ss .
docker build -t dev/httpd72ss .



docker-compose -f myweb.yml down
docker-compose -f myweb.yml up -d

docker-compose -f myweb72.yml down
docker-compose -f myweb72.yml up -d

# gist
https://gist.github.com/iamchkchk/492cffb52cf269ed50fa39236e91d688
https://gist.github.com/iamchkchk/a28340b24515f1e34ecc590a7b8d98e6
https://gist.github.com/iamchkchk/082d9151e77a132585e6223117b34add


# mysql 5.7
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'root';
FLUSH PRIVILEGES;

