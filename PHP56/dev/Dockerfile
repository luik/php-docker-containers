FROM php:5.6-apache

# PHP extension

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libicu-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libxslt1-dev \
        vim \
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
                   xmlrpc \
                && pecl install redis-4.3.0 && docker-php-ext-enable redis \
                && pecl install xdebug-2.5.5 && docker-php-ext-enable xdebug
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

