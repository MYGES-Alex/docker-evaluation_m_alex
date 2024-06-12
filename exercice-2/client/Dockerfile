# client/Dockerfile

# Utiliser l'image officielle PHP avec Apache
FROM php:8.2-apache

# Installer les extensions nécessaires
RUN apt-get update && apt-get install -y libmariadb-dev \
    && docker-php-ext-install mysqli pdo_mysql \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Copier le code source dans le conteneur
COPY . /var/www/html/

# Donner les droits corrects
RUN chown -R www-data:www-data /var/www/html
