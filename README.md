# docker

docker run --name env71 --link mysql57:mysql --link redis40:redis -it -d -p 80:80 -v /c/wamp/www:/var/www/html -v /c/Users/1111003/dockerbase/apache2:/var/log/apache2 dev/apachephp71:latest

docker run --name env56 --link mysql57:mysql --link redis40:redis -it -d -p 80:80 -v /c/wamp/www:/var/www/html -v /c/Users/1111003/dockerbase/apache2:/var/log/apache2 dev/apachephp56:latest


docker run --name mysql57 -v /d/dockerbase/mysql/data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=root -d mysql

docker run -it --link mysql57:mysql --rm mysql sh -c 'exec mysql -h"$MYSQL_PORT_3306_TCP_ADDR" -P"$MYSQL_PORT_3306_TCP_PORT" -uroot -p'


docker run --name redis -p 6379:6379 -d redis40

docker run -it --link redis40:redis --rm redis redis-cli -h redis -p 6379


