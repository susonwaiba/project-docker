FROM php:7.4-fpm

RUN apt-get update && apt-get upgrade -y

# Installing required packages
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y apt-utils
RUN apt-get install -y apt-transport-https
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y libicu-dev \
    libonig-dev \
    libzip-dev \
    libpng-dev
RUN apt-get install -y libcurl4-openssl-dev \
    pkg-config \
    libssl-dev

# Installing extensions
RUN docker-php-ext-install pdo_mysql intl mbstring zip exif pcntl bcmath opcache gd

# Installing others dependencies
RUN pecl install redis
RUN docker-php-ext-enable redis
RUN pecl install mongodb-1.8.0
RUN docker-php-ext-enable mongodb

CMD ["php-fpm", "-F"]
