ARG PHP_VERSION=7.1.16

FROM php:${PHP_VERSION}-fpm

LABEL maintainer="pingink <pingink@163.com>"

RUN apt-get update && apt-get install --yes zip unzip
RUN curl -sS https://getcomposer.org/installer | php && mv composer.phar /usr/bin/composer && chmod u+x /usr/bin/composer && composer config -g repo.packagist composer https://packagist.phpcomposer.com
ADD src/php-${PHP_VERSION}.tar.gz /var
RUN cd /var/php-${PHP_VERSION}/ext/bcmath && /usr/local/bin/phpize && ./configure --with-php-config=/usr/local/bin/php-config && make && make install &&\
    rm -rf /var/php-${PHP_VERSION} &&\
    rm -rf /usr/local/etc/php-fpm.d/www.conf

EXPOSE 9000

CMD ["php-fpm", "-R"]
