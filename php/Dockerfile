FROM php:7.4-fpm-buster

COPY php.ini /usr/local/etc/php/conf.d/docker-php-config.ini

RUN apt-get update && apt-get install -y \
    gnupg \
    g++ \
    procps \
    openssl \
    git \
    unzip \
    zlib1g-dev \
    libzip-dev \
    libfreetype6-dev \
    libpng-dev \
    libjpeg-dev \
    libicu-dev  \
    libonig-dev \
    libxslt1-dev \
    acl \
    git \
    && echo 'alias sf="php bin/console"' >> ~/.bashrc

RUN docker-php-ext-configure gd --with-jpeg --with-freetype 

RUN docker-php-ext-install \
    pdo pdo_mysql mysqli  zip xsl gd intl opcache exif mbstring

RUN ln -snf /usr/share/zoneinfo/Europe/Kiev /etc/localtime && echo Europe/Kiev > /etc/timezone \
    && printf '[PHP]\ndate.timezone = "%s"\n', Europe/Kiev > /usr/local/etc/php/conf.d/tzone.ini \
    && "date"
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
WORKDIR /var/www/symfony5-project
