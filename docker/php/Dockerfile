FROM php:8.1-fpm-alpine

# Set working directory
WORKDIR /var/www

# Install dependencies
RUN apk update && apk add --no-cache --virtual .build-deps $PHPIZE_DEPS \
    libzip-dev zip
# Install extensions
RUN docker-php-ext-install pdo_mysql zip
# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
# Add user for laravel application
#RUN groupadd -g 1000 www
#RUN useradd -u 1000 -ms /bin/bash -g www www
# Copy existing application directory contents
COPY php-app /var/www
# Copy existing application directory permissions
#COPY --chown=www:www . /var/www
# Change current user to www
#USER www
# Expose port 9000 and start php-fpm server
EXPOSE 9000
CMD ["php-fpm"]