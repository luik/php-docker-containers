FROM php:7.3-apache

# PHP extension

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libicu-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng-dev \
        libxslt1-dev \
        vim \
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
                && pecl install xdebug && docker-php-ext-enable xdebug
RUN echo "xdebug.remote_enable=1" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
                && echo "xdebug.remote_port=9000" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
                && echo "xdebug.idekey=PHPSTORM" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
                && echo "xdebug.max_nesting_level=1000" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
                && echo "xdebug.remote_host=172.17.0.1" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
                && chmod 666 /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
                && a2enmod rewrite
#         && mkdir /var/www/moodledata && chown www-data:www-data /var/www/moodledata
COPY php.ini /usr/local/etc/php/php.ini
EXPOSE 80
