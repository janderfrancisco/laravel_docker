FROM php:7.4-fpm-alpine

# install 
RUN apk add --no-cache shadow openssl bash mysql-client nodejs npm

# install php extensions 
RUN docker-php-ext-install pdo pdo_mysql

# install dockerize
ENV DOCKERIZE_VERSION v0.6.1
RUN wget https://github.com/jwilder/dockerize/releases/download/$DOCKERIZE_VERSION/dockerize-alpine-linux-amd64-$DOCKERIZE_VERSION.tar.gz \
    && tar -C /usr/local/bin -xzvf dockerize-alpine-linux-amd64-$DOCKERIZE_VERSION.tar.gz \
    && rm dockerize-alpine-linux-amd64-$DOCKERIZE_VERSION.tar.gz



# acessa a pasta www, para rodar os comandos 
WORKDIR /var/www

#apaga a pasta html do container
RUN rm -rf /var/www/html

# cria link simbolico da pasta html para a pasta public	
RUN ln -s public html


#RUN chown -R www-data:www-data /var/www
#RUN chmod 755 /usr/local/bin/dockerize
 

 # install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer


RUN usermod -u 1000 www-data
USER www-data


EXPOSE 9000

ENTRYPOINT ["php-fpm"]
 
