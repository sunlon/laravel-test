# Use the official PHP image
FROM php:8.2-cli

# Set working directory
WORKDIR /var/www/html

# Install dependencies
RUN apt-get update && apt-get install -y \
    git \
    libzip-dev \
    unzip

# Install PHP extensions
RUN docker-php-ext-install pdo_mysql zip

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Copy Laravel application files
COPY . .

# Install PHP dependencies
#RUN composer install --no-dev --optimize-autoloader

# Expose port 8080 (required by Cloud Run)
#EXPOSE 80

# Run Laravel application
CMD php artisan serve 
