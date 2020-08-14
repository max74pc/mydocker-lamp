FROM phusion/baseimage:latest

# Add the PHP ppa
RUN apt install -y software-properties-common && \
    add-apt-repository -y ppa:ondrej/php

# Install "PHP Extentions", "libraries", "Software's"
RUN apt-get update && \
    apt-get install -y --allow-downgrades --allow-remove-essential \
        --allow-change-held-packages \
        php7.4-cli \
        php7.4-common \
        php7.4-curl \
        php7.4-intl \
        php7.4-json \
        php7.4-xml \
        php7.4-mbstring \
        php7.4-mysql \
        php7.4-zip \
        php7.4-memcached \
        php7.4-cgi \
        php7.4-gd \
        php7.4-dev \
        pkg-config \
        php7.4-imagick \
        curl \
        vim \
        apt-utils \
        zip unzip && \
        php -m | grep -q 'zip' \
    && apt-get autoremove -y \
    && apt-get clean

# Install composer and add its bin to the PATH.
RUN curl -s http://getcomposer.org/installer | php && \
    echo "export PATH=${PATH}:/var/www/vendor/bin" >> ~/.bashrc && \
    mv composer.phar /usr/local/bin/composer

# Working dir
WORKDIR /var/www/html
