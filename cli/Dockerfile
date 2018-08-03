FROM php:7.0-cli

# Install dependencies
RUN apt-get update \
  && apt-get install -y \
    git \
    libfreetype6-dev \
    libicu-dev \
    libjpeg62-turbo-dev \
    libmcrypt-dev \
    libpng-dev \
    libxslt1-dev \
    mysql-client \
    zip

# Install required PHP extensions
RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ && \
    docker-php-ext-install bcmath dom gd intl mbstring mcrypt pdo_mysql soap sockets xsl zip && \
    pecl channel-update pecl.php.net && \
    yes | pecl install xdebug-2.6.1 && \
    docker-php-ext-enable xdebug

ENV COMPOSER_ALLOW_SUPERUSER 1

VOLUME /root/.composer/cache

# Get composer installed to /usr/local/bin/composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
