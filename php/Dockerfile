FROM php:7.0-fpm
COPY ./apt_sources.list /etc/apt/sources.list.new
RUN cat /etc/apt/sources.list.new >> /etc/apt/sources.list \
&& apt-get update
RUN apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng12-dev 

RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
&& docker-php-ext-install opcache pdo_mysql mbstring gd
COPY ./www.conf /usr/local/etc/php-fpm.d/www.conf
RUN echo "opcache.revalidate_freq=30" >> /usr/local/etc/php/conf.d/docker-php-ext-opcache.ini
