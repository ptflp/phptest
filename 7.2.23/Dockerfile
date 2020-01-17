FROM php:7.2.23-fpm-stretch

RUN DEBIAN_FRONTEND=noninteractive apt-get update && apt-get -y install \
    imagemagick libmagickwand-dev libgmp-dev tzdata git socat \
    && pecl install imagick-beta redis-4.2.0 \
    && curl -sS https://getcomposer.org/installer | php \
    && mv composer.phar /usr/local/bin/composer \
	&& composer global require "fxp/composer-asset-plugin:~1.4.2" \
	&& composer global require hirak/prestissimo
    && docker-php-ext-install pdo_mysql exif shmop bcmath gmp zip \
    && docker-php-ext-enable redis imagick \
    && docker-php-ext-install intl
    && docker-php-ext-configure gd \
        --with-gd \
        --with-freetype-dir=/usr/include/ \
        --with-png-dir=/usr/include/ \
        --with-jpeg-dir=/usr/include/
    && rm -rf /var/lib/apt/lists/*```