FROM php:fpm

RUN apt-get update && apt-get install -y \
        curl \
        wget \
        git \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
       	libpng-dev \
       	libonig-dev \
       	libzip-dev \
       	libmcrypt-dev \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd iconv mbstring \
    && docker-php-ext-install pdo pdo_mysql

RUN wget https://raw.githubusercontent.com/composer/getcomposer.org/76a7060ccb93902cd7576b67264ad91c8a2700e2/web/installer -O - -q | php -- --quiet

WORKDIR /var/www/app

CMD ["php-fpm"]