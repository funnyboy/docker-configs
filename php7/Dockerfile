FROM php:7.0-fpm

MAINTAINER Dmitry Zaiets "funnyboy1190@gmail.com"

RUN apt-get update && apt-get install -my \
        curl \
        wget \
        vim-common \
        mc \
        libxml2-dev \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng12-dev \
        ssmtp \
    && docker-php-ext-install -j$(nproc) iconv mcrypt bcmath mbstring pdo pdo_mysql soap \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd

# Install composer
RUN bash -c "wget http://getcomposer.org/composer.phar && mv composer.phar /usr/local/bin/composer"
RUN bash -c "chmod 0777 /usr/local/bin/composer"

# Install XDebug
RUN pecl install xdebug-2.4.0
RUN docker-php-ext-enable xdebug
RUN docker-php-ext-install pcntl

ADD xdebug.ini /usr/local/etc/php/conf.d/
ADD config.ini /usr/local/etc/php/conf.d/

RUN cp /etc/ssmtp/ssmtp.conf /etc/ssmtp/ssmtp.conf.bak
COPY ssmtp.conf /etc/ssmtp/ssmtp.conf

ADD php-fpm.conf /etc/php7/php-fpm.conf
ADD www.conf /etc/php7/php-fpm.d/www.conf

# Need for MC
RUN bash -c "export TERM=xterm"

RUN useradd -ms /bin/bash funnyboy
USER funnyboy
VOLUME /var/www/projects

