FROM richarvey/nginx-php-fpm:latest

# WORKDIR /var/www/html/web

RUN apk update && apk add wget && apk add unzip
RUN   wget https://github.com/zeppaman/WpGet-Private-wordpress-plugin-repository/releases/download/v1.0.1/web-installer.zip -O /tmp/package.zip \
&& unzip /tmp/package.zip -d /var/www/html

