# Use the official Jenkins LTS image as a base
FROM jenkins/jenkins:lts

# Switch to root user for installation
USER root
RUN apt-get update \
    && apt-get install -y \
        software-properties-common \
        apt-transport-https \
        lsb-release \
        wget

# Install PHP 8.2
RUN wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg \
    && echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list \
    && apt-get update \
    && apt-get install -y \
        php8.2 \
        php8.2-cli \
        php8.2-common \
        php8.2-mbstring \
        php8.2-xml \
        php8.2-zip \
        php8.2-intl \
        php8.2-mysql \
        php8.2-sqlite3

# install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# install dependencies
RUN apt-get update && apt-get install -y \
    libpng-dev \
    zlib1g-dev \
    libxml2-dev \
    libzip-dev \
    libonig-dev \
    zip \
    curl \
    unzip \
    jpegoptim \
    optipng \
    pngquant \
    gifsicle \
    webp 
    
# Switch back to the Jenkins user
USER jenkins

