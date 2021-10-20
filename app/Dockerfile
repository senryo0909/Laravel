FROM php:7.4-fpm

COPY php.ini /usr/local/etc/php/

RUN apt-get update \
&& apt-get install -y libzip-dev libpq-dev \
&& docker-php-ext-install zip pdo_mysql pdo_pgsql

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
&& php composer-setup.php \
&& php -r "unlink('composer-setup.php');" \
&& mv composer.phar /usr/local/bin/composer

RUN apt-get install -y libpq-dev \
&& docker-php-ext-install pdo_mysql pdo_pgsql

ENV COMPOSER_HOME /composer
ENV PATH $PATH:/composer/vendor/bin