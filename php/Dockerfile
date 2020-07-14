FROM php:7.4-fpm

# Installing dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    mariadb-client \
    libpng-dev \
    libjpeg62-turbo-dev \
    libfreetype6-dev \
    libmagickwand-dev \
    libzip-dev \
    locales \
    jpegoptim \
    optipng \
    pngquant \
    gifsicle \
    zip \
    unzip \
    wget \
    vim \
    git \
    libonig-dev \
    libcurl4-openssl-dev \
    libssl-dev \
    screenfetch

# Installing composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Installing extensions
RUN docker-php-ext-install pdo_mysql intl mbstring zip exif pcntl bcmath opcache gd

# Installing others dependencies
RUN pecl install imagick
RUN docker-php-ext-enable imagick
RUN pecl install redis
RUN docker-php-ext-enable redis
RUN pecl install mongodb-1.8.0beta2
RUN docker-php-ext-enable mongodb

# Installing symfony cli
RUN wget https://get.symfony.com/cli/installer -O - | bash
RUN echo 'export PATH="$HOME/.symfony/bin:$PATH"' >> ~/.bashrc

# Clear cache
#RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# RUN php-settings-update "short_open_tag" "Off"

# Setup working directory
RUN mkdir /var/www/project