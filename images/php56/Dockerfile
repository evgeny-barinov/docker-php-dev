FROM php:5.6-fpm

RUN apt-get update && apt-get install -y --no-install-recommends apt-utils \
        openssl \
        libssl-dev \
        pkg-config \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng12-dev \
        g++ \
        libicu-dev \
        libxslt1-dev \
        libxml2-dev \
    && docker-php-ext-install -j$(nproc) iconv mcrypt pdo_mysql mysqli gd exif bcmath\
    intl xsl soap gettext sockets simplexml xmlwriter zip opcache \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    --with-png-dir=/usr/include/ --with-zlib-dir \
    && docker-php-ext-install -j$(nproc) gd

RUN pecl install redis \
    && pear install mail \
    && pear install Mail_Mime \
    && pear install Net_Socket \
    && pear install Net_SMTP \
    && pecl install mongodb \
    && docker-php-ext-enable redis mongodb

#ADD php.ini /usr/local/etc/php/conf.d/40-custom.ini
#RUN sed -i -e "s/listen\s*=\s*127.0.0.1:9000/listen = [::]:9000/g" /usr/local/etc/php-fpm.d/www.conf  \
#&& sed -i -e "s/;chdir\s*=\s*\/var\/www/chdir = \/usr\/share\/nginx\/html/g" /usr/local/etc/php-fpm.d/www.conf \
