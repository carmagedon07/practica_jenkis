FROM php:8.2-apache

# Habilitar mod_rewrite
RUN a2enmod rewrite

# Instalar dependencias del sistema para extensiones
RUN apt-get update && apt-get install -y \
    zlib1g-dev \
    libicu-dev \
    libxml2-dev \
    libpq-dev \
    vim \
 && docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql \
 && docker-php-ext-install pdo pdo_mysql pdo_pgsql zip intl soap opcache \
 && docker-php-ext-configure pdo_mysql --with-pdo-mysql=mysqlnd

# Copiar tu app si corresponde, ej:
# COPY ./src /var/www/html

EXPOSE 80
