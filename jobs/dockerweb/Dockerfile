FROM php:8.2-apache

# 1. habilitar mod_rewrite de Apache
RUN a2enmod rewrite

# 2. instalar dependencias del sistema necesarias para compilar las extensiones PHP
#    incluimos libzip-dev para que la extensión zip compile
RUN apt-get update && apt-get install -y \
    zlib1g-dev \
    libicu-dev \
    libxml2-dev \
    libpq-dev \
    libzip-dev \
    libssl-dev \
    vim \
 && docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql \
 && docker-php-ext-configure pdo_mysql --with-pdo-mysql=mysqlnd \
 && docker-php-ext-install \
    pdo \
    pdo_mysql \
    pdo_pgsql \
    zip \
    intl \
    soap \
    opcache \
 && rm -rf /var/lib/apt/lists/*

# (opcional) si tenés código de la app en el repo, acá lo copiás:
# COPY ./src /var/www/html

EXPOSE 80
