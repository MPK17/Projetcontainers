# Utilisez une image de base avec PHP et Apache
FROM php:8.1-apache

# Copiez tous les fichiers de l'application web dans le conteneur
COPY . /var/www/html

# Installez les dépendances PHP nécessaires à l'application web
RUN apt-get update && \
    apt-get install -y \
        libicu-dev \
        libpq-dev \
        && \
    docker-php-ext-install \
        pdo \
        pdo_pgsql \
        intl \
        && \
    pecl install \
        xdebug \
        && \
    docker-php-ext-enable \
        xdebug

# Activez les modules Apache nécessaires à l'application web
RUN a2enmod rewrite && \
    service apache2 restart

# Exposez le port 80 pour permettre l'accès à l'application web
EXPOSE 80

