FROM php:8.2-fpm
# Install system dependencies
RUN apt-get update && apt-get install -y \
    git \
    curl \
    libpng-dev \
    libonig-dev \
    libxml2-dev \
    zip \
    libpq-dev \
    unzip \ 
    supervisor

# Clear cache
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Install PHP extensions
RUN docker-php-ext-install pdo_pgsql mbstring exif pcntl bcmath gd

# Install the phpredis extension via PECL
RUN pecl install redis \
    && docker-php-ext-enable redis

RUN mkdir -p /var/log/supervisor
COPY ./config/horizon-worker.conf /etc/supervisor/conf.d/horizon-worker.conf
COPY ./config/rabbitmq-worker.conf /etc/supervisor/conf.d/rabbitmq-worker.conf
CMD ["/usr/bin/supervisord"]
