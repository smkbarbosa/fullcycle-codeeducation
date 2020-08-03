FROM php:7.3.6-fpm-alpine3.9
RUN apk add bash mysql-client 
RUN apk add shadow
RUN docker-php-ext-install pdo pdo_mysql 

ENV DOCKERIZE_VERSION v0.6.1
RUN wget https://github.com/jwilder/dockerize/releases/download/$DOCKERIZE_VERSION/dockerize-linux-amd64-$DOCKERIZE_VERSION.tar.gz \
    && tar -C /usr/local/bin -xzvf dockerize-linux-amd64-$DOCKERIZE_VERSION.tar.gz \
    && rm dockerize-linux-amd64-$DOCKERIZE_VERSION.tar.gz

RUN usermod -u 1000 www-data

RUN chmod 755 /usr/local/bin/dockerize

WORKDIR /var/www
RUN rm -rf /var/www/html

COPY ./.docker/app/.env.tmpl .env.tmpl

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN ln -s public html
USER www-data

EXPOSE 9000
ENTRYPOINT ["php-fpm"]
