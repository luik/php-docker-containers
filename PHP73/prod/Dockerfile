FROM php:7.3-apache

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libicu-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng-dev \
        libxslt1-dev \
        vim \
        libzip-dev \
        && docker-php-ext-configure \
                   gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
         && docker-php-ext-configure opcache --enable-opcache \
        && docker-php-ext-install \
                   gd \
                   intl \
                   mbstring \
                   pdo_mysql \
                   mysqli \
                   xsl \
                   soap \
                   bcmath \
                   opcache \
                   xmlrpc \
                   zip \
                && pecl install redis && docker-php-ext-enable redis \
                && a2enmod rewrite
#        && mkdir /var/www/moodledata && chown www-data:www-data /var/www/moodledata
# COPY php.ini /usr/local/etc/php/php.ini
EXPOSE 80
