ARG PHP_VERSION="7.4"

FROM php:${PHP_VERSION}-fpm

# Install the PHP extention using "apt"
RUN apt update && \
  apt install -y --no-install-recommends \
    apt-utils \
    curl \
    libmemcached-dev \
    libzip-dev \
    libz-dev \
    libpq-dev \
    libjpeg-dev \
    libmagickwand-dev \
    libmagickcore-dev \
    libpng-dev \
    libfreetype6-dev \
    libssl-dev \
    libmcrypt-dev \
    mcrypt \
    zlib1g-dev \
    libicu-dev \
    libpq-dev \
    libssl-dev \
    g++ \
  && apt autoremove -y \
  && apt clean

# Install the PHP extention using "docker-php"
RUN docker-php-ext-configure intl \
  && docker-php-ext-install intl \
  && docker-php-ext-install zip \
  && docker-php-ext-install pdo_mysql \
  && rm -rf /var/lib/apt/lists/*

COPY configurations/php.ini /usr/local/etc/php/php.ini

# Install 'xdebug-2.5.5' for PHP 7
RUN pecl install xdebug \
  && docker-php-ext-enable xdebug

RUN echo "zend_extension=$(find /usr/local/lib/php/extensions/ -name xdebug.so)" >> /usr/local/etc/php/php.ini