FROM php:8.1.0-fpm

# install composer
RUN cd /usr/bin && curl -s http://getcomposer.org/installer | php && ln -s /usr/bin/composer.phar /usr/bin/composer
RUN apt-get update \
    && apt-get install -y \
    git \
    zip \
    unzip \
    vim

# install xdebug
RUN apt-get -y update && \
    pecl install xdebug && \
    docker-php-ext-enable xdebug && \
    mv /etc/localtime /etc/localtime.org && \
    ln -s /usr/share/zoneinfo/Japan /etc/localtime && \
    echo xdebug.remote_enable=1 >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini && \
    echo xdebug.remote_host=localhost >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini && \
    echo xdebug.remote_port=9001 >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini && \
    echo xdebug.remote_autostart=true >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini


RUN apt-get update \
    && apt-get install -y libpq-dev \
    && docker-php-ext-install pdo_mysql pdo_pgsql


WORKDIR /var/www/html
