FROM php:8.2.11-fpm

# Set environment variables
ENV PHP_OPCACHE_ENABLE=0
ENV PHP_OPCACHE_ENABLE_CLI=0
ENV PHP_OPCACHE_VALIDATE_TIMESTAMPS=0
ENV PHP_OPCACHE_REVALIDATE_FREQ=0

# Install composer
RUN echo "\e[1;33mInstall COMPOSER\e[0m"
RUN cd /tmp \
    && curl -sS https://getcomposer.org/installer | php \
    && mv composer.phar /usr/local/bin/composer 

RUN docker-php-ext-install pdo pdo_mysql

RUN apt-get update

# Install useful tools
RUN apt-get -y install apt-utils nano wget dialog vim

# Install important libraries
RUN echo "\e[1;33mInstall important libraries\e[0m"
RUN apt-get -y install --fix-missing \
    apt-utils \
    build-essential \
    git \
    curl \
    libcurl4 \
    libcurl4-openssl-dev \
    zlib1g-dev \
    libzip-dev \
    zip \
    libbz2-dev \
    locales \
    libmcrypt-dev \
    libicu-dev \
    libonig-dev \
    libxml2-dev  
    
   # nginx

    
# RUN echo "\e[1;33mInstall important docker dependencies\e[0m"
# RUN docker-php-ext-install \
#     exif \
#     pcntl \
#     bcmath \
#     ctype \
#     curl \
#     iconv \
#     xml \
#     soap \
#     pcntl \
#     mbstring \
#     tokenizer \
#     bz2 \
#     zip \
#     intl

# Install Postgre PDO
RUN apt-get install -y libpq-dev \
    && docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql \
    && docker-php-ext-install pdo pdo_pgsql pgsql \
    bcmath \
    ctype \
    xml \
    mbstring \
    opcache

# Set up Nginx server
#COPY nginx/default.conf /etc/nginx/sites-available/default
#RUN ln -s /etc/nginx/sites-available/default /etc/nginx/sites-enabled/default

# RUN rm /etc/nginx/sites-enabled/default && \
#    ln -s /etc/nginx/sites-available/default /etc/nginx/sites-enabled/default
# Expose ports
#EXPOSE 80

# Start Nginx and PHP-FPM
#CMD service nginx start && php-fpm