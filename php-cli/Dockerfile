FROM php:7.4-cli

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

# Installing other packages
RUN apt-get update
RUN apt-get install -y git
RUN apt-get install -y vim
RUN apt-get install -y zip
RUN apt-get install -y unzip
RUN apt-get install -y wget
RUN apt-get install -y screenfetch

# Updating php.ini
ADD conf/php.ini /usr/local/etc/php/php.ini

# Installing composer
VOLUME /root/.composer/cache
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Installing symfony cli
RUN wget https://get.symfony.com/cli/installer -O - | bash
RUN echo 'export PATH="$HOME/.symfony/bin:$PATH"' >> ~/.bashrc+

CMD ["bash"]
