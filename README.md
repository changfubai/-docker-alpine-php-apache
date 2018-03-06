# docker-alpine-php-apache

含php和apache的docker镜像，用于部署基于typecho框架的个人博客
解决后台管理出现Call to undefined function token_get_all()错误的情况
增加了	php7-tokenizer

## mysql

docker pull mysql:5.7.19

mkdir -p /root/web/mysql

docker run -e MYSQL_ROOT_PASSWORD='yourpassword' -d -p 127.0.0.1:3306:3306 --name mysql-5.7.19 -v /root/web/mysql:/var/lib/mysql mysql:5.7.19

docker stop mysql-5.7.19

docker rm mysql-5.7.19

docker run -d --restart=always -p 127.0.0.1:3306:3306 --name mysql-5.7.19 -v /root/web/mysql:/var/lib/mysql mysql:5.7.19

## docker-alpine-php-apache

docker pull changfubai/docker-alpine-php-apache

docker run -d --restart=always --link mysql-5.7.19:mysql -p 8088:80 --name www.changfubai.com -v /root/web/www/www.changfubai.com:/var/www/html changfubai/docker-alpine-php-apache

我的个人网站： https://changfubai.com

参考自：https://github.com/ilanyu/docker-php-apache
