FROM php:7.4-apache

RUN a2enmod rewrite

RUN apt-get update && apt-get install -y git unzip zip nano

COPY --from=mlocati/php-extension-installer /usr/bin/install-php-extensions /usr/local/bin

RUN install-php-extensions gd pdo_mysql bcmath zip intl opcache mysqli

COPY --from=composer:2.0 /usr/bin/composer /usr/local/bin/composer



RUN apt-get install -y curl \
    && curl -sS https://get.symfony.com/cli/installer | bash \
    && curl -sL https://deb.nodesource.com/setup_12.x | bash - \
    && apt-get install -y nodejs \
    && curl -L https://www.npmjs.com/install.sh | sh



RUN mv /root/.symfony/bin/symfony /usr/local/bin/symfony