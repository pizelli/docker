FROM php:7.4-apache

MAINTAINER Giovanni Pizelli <pizelg@gmail.com>

ADD https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions /usr/local/bin/

RUN chmod +x /usr/local/bin/install-php-extensions && \
    install-php-extensions gd xdebug-^2 bcmath bz2 intl zip pdo_mysql exif @composer

RUN a2enmod rewrite

COPY ./vhost.conf /etc/apache2/sites-available/000-default.conf

EXPOSE 80

WORKDIR /var/www/html

#ENTRYPOINT /etc/init.d/apache2 start && /bin/bash
ENTRYPOINT ["docker-php-entrypoint"]

#CMD ["true"]
CMD ["apache2-foreground"]
