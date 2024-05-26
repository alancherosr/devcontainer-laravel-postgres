FROM php:8.3-fpm

# Install system dependencies
RUN apt-get update && apt-get install -y \
    libpng-dev \
    libonig-dev \
    libxml2-dev \
    zip \
    unzip \
    git \
    curl \
    sudo \
    libicu-dev \
    libpq-dev \
    libzip-dev \
    # Install Node.js and npm
    nodejs \
    npm

# Install PHP extensions
RUN docker-php-ext-install pdo_mysql mbstring exif pcntl bcmath gd intl pdo_pgsql pgsql zip

# Get latest Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Set working directory
WORKDIR /var/www

# Clear cache
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Create a new user 'devuser' with /bin/bash as the shell
RUN useradd -u 1000 -m -s /bin/bash devuser

# Add 'devuser' to the 'www-data' group so it can have appropriate permissions
RUN usermod -a -G www-data devuser && \
    # Allow 'devuser' to run sudo commands without a password
    echo 'devuser ALL=(ALL) NOPASSWD: ALL' >> /etc/sudoers

# Use 'devuser' as the default user
USER devuser
