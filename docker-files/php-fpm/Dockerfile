ARG PHP_VERSION=7.3
ARG PHP_INSTALL_XDEBUG=false

FROM php:${PHP_VERSION}-fpm

EXPOSE 9000

RUN usermod -u 1000 www-data

RUN apt-get update \
    && pecl channel-update pecl.php.net

RUN docker-php-ext-install \
    bcmath \
    mysqli \
    opcache \
    pdo_mysql \
    pcntl

# RUN apt-get install -y libgd-dev libpng-dev libjpeg-dev libfreetype6-dev \
#    && docker-php-ext-configure gd --with-gd --with-png-dir=/usr/include --with-jpeg-dir=/usr/include --with-freetype-dir=/usr/include/freetype2 \
#    && docker-php-ext-install gd

RUN apt-get install -y libicu-dev \
    && docker-php-ext-configure intl \
    && docker-php-ext-install intl

RUN apt-get install -y libzip-dev \
    && docker-php-ext-configure zip --with-libzip \
    && docker-php-ext-install zip

RUN pecl install mongodb \
    && docker-php-ext-enable mongodb

RUN pecl install redis \
    && docker-php-ext-enable redis

#RUN apt-get install -y libmemcached-dev zlib1g-dev \
#    && pecl install memcached \
#    && docker-php-ext-enable memcached

RUN if [ ${PHP_INSTALL_XDEBUG} = true ]; then \
    pecl install xdebug; \
    docker-php-ext-enable xdebug; \
fi

RUN apt-get clean

COPY php.ini /usr/local/etc/php/
COPY conf.d/xdebug.ini /usr/local/etc/php/conf.d/
COPY php-fpm.d/www.conf /usr/local/etc/php-fpm.d/

WORKDIR /var/www/acme

CMD ["php-fpm"]
