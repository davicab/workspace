
  
FROM php:8.1.0-fpm

# Install system dependencies
RUN apt-get update && apt-get install -y git

# Install PHP extensions
RUN apt-get update \
    && apt-get install -y gnupg curl wget ca-certificates unzip lsb-release \
    && wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | apt-key add - \
    && echo "deb http://apt.postgresql.org/pub/repos/apt/ `lsb_release -cs`-pgdg main" | tee  /etc/apt/sources.list.d/pgdg.list \
    && curl -sL https://deb.nodesource.com/setup_16.x | bash - \
    && apt-get install -y \
        libicu-dev \
        libpq-dev \
        libzip-dev \
        nodejs \
        postgresql-client-14 \
    && pecl install redis \
    && docker-php-ext-enable redis \
    && docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql \
    && docker-php-ext-install intl pdo pdo_pgsql pdo_mysql pgsql zip bcmath pcntl exif \
    && php -r "readfile('http://getcomposer.org/installer');" | php -- --install-dir=/usr/bin/ --filename=composer \
    && npm install -g npm \
    && apt-get -y autoremove \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* \
    && chown -R www-data:www-data /var/www

RUN touch /usr/local/etc/php/conf.d/uploads.ini \
    && echo "upload_max_filesize = 50M\npost_max_size = 50M\nmax_execution_time = 600\nmax_input_vars = 4000" >> /usr/local/etc/php/conf.d/uploads.ini

RUN echo "xdebug.remote_autostart=1" | tee -a /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini > /dev/null && \
    echo "xdebug.remote_enable=1" | tee -a /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini > /dev/null && \
    echo "xdebug.remote_host=192.168.1.223" | tee -a /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini > /dev/null