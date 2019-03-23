FROM php:5.6-apache

# PHP extension

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libicu-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng-dev \
        libxslt1-dev \
        vim \
        libmemcached11 libmemcachedutil2 build-essential libmemcached-dev libz-dev \
        && docker-php-ext-configure \
                   gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
        && docker-php-ext-configure opcache --enable-opcache \
        && docker-php-ext-install \
                   gd \
                   intl \
                   mbstring \
                   mcrypt \
                   pdo_mysql \
                   mysqli \
                   xsl \
                   zip \
                   soap \
                   bcmath \
                   opcache \
        && pecl install memcached-2.2.0 \
        && docker-php-ext-enable memcached 
#        && a2enmod rewrite && mkdir /var/www/moodledata && chown www-data:www-data /var/www/moodledata
COPY php.ini /usr/local/etc/php/
EXPOSE 80
