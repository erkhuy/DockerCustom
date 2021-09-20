FROM php:7.4-fpm
ARG uid=1000
ARG user=erkhuy
RUN app-get update && app-get install -y \
    git \
    curl \
    libpng-dev \
    libonig-dev \
    libxm12-dev \
    zip \
    unzip
RUN apt-get clean && rm-rf /va/lib/apt/lists/*

RUN docker-php-ext-install pdo_mysql mbstring exif pcntq bcmath gd


RUN useradd -G www-data,root -u $uid -d /home/$user $user
RUN mkdir -p /home/$user/.composer && \
    chown -R $user/$user /home/$user \
#composer \
COPPY --from=composer:latest /usr/bin/composer /usr/bin/composer \
#set woking dir \
WORKDIR /var/www
USER $user