ARG PHP_VERSION=7.1.16

FROM php:${PHP_VERSION}-fpm

LABEL maintainer="pingink <pingink@163.com>"

# base
RUN rm -rf /usr/local/etc/php-fpm.d/www.conf
RUN docker-php-ext-install mysqli pdo pdo_mysql opcache bcmath mbstring sockets

# zip
RUN apt-get update -y && apt-get install -y \
    libzip-dev \
    unzip \
  && docker-php-ext-install zip

#gd
RUN apt-get update -y && apt-get install -y \
    zlib1g-dev \
    libxpm-dev \
    libwebp-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    libfreetype6-dev \
  && docker-php-ext-configure gd --with-gd --with-webp-dir --with-jpeg-dir --with-png-dir --with-zlib-dir --with-xpm-dir --with-freetype-dir --enable-gd-native-ttf \
  && docker-php-ext-install gd

# composer
RUN curl -sS https://getcomposer.org/installer | php && mv composer.phar /usr/bin/composer && chmod u+x /usr/bin/composer && composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/

EXPOSE 9000

CMD ["php-fpm", "-R"]
