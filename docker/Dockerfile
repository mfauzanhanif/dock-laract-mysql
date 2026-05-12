FROM php:8.5-fpm

# Menginstal system dependencies
RUN apt-get update && apt-get install -y \
    git \
    curl \
    libpng-dev \
    libonig-dev \
    libxml2-dev \
    libzip-dev \
    zip \
    unzip \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

# Menginstal PHP extensions yang dibutuhkan Laravel
RUN docker-php-ext-install pdo_mysql mbstring exif pcntl bcmath gd zip

# Menginstal Composer (Latest)
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Menginstal Node.js 24.15.0 LTS secara presisi
RUN curl -fsSLO --compressed "https://nodejs.org/dist/v24.15.0/node-v24.15.0-linux-x64.tar.xz" \
    && tar -xJf "node-v24.15.0-linux-x64.tar.xz" -C /usr/local --strip-components=1 --no-same-owner \
    && rm "node-v24.15.0-linux-x64.tar.xz"

# Mengonfigurasi Composer Home dan menginstal Laravel Installer
ENV COMPOSER_HOME="/tmp/composer"
ENV PATH="${COMPOSER_HOME}/vendor/bin:${PATH}"
RUN composer global require laravel/installer

WORKDIR /var/www