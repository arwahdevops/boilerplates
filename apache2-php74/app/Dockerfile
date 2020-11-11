FROM ubuntu:bionic
MAINTAINER rikipermana <rikipermana@live.com>

ENV OS_LOCALE="en_US.UTF-8"
RUN apt-get update && apt-get install -y locales && locale-gen ${OS_LOCALE}
ENV LANG=${OS_LOCALE} \
    LANGUAGE=${OS_LOCALE} \
    LC_ALL=${OS_LOCALE} \
    DEBIAN_FRONTEND=noninteractive

ENV APACHE_CONF_DIR=/etc/apache2 \
    PHP_CONF_DIR=/etc/php/7.4 \
    PHP_DATA_DIR=/var/lib/php

RUN     \
        BUILD_DEPS='software-properties-common' \
    && dpkg-reconfigure locales \
        && apt-get install --no-install-recommends -y $BUILD_DEPS \
        && add-apt-repository -y ppa:ondrej/php \
        && add-apt-repository -y ppa:ondrej/apache2 \
        && apt-get update \
    && apt-get install -y \
    nano \
    cron \
    curl \
    apache2 \
    libapache2-mod-php7.4 \
    php7.4-cli \
    php7.4-readline \
    php7.4-mbstring \
    php7.4-zip \
    php7.4-intl \
    php7.4-xml \
    php7.4-json \
    php7.4-curl \
    php7.4-gd \
    php7.4-pgsql \
    php7.4-gd \
    php7.4-mysql \
    php-pear \
    # Apache settings
    && a2enmod rewrite php7.4 \
        # Install composer
        && curl -sS https://getcomposer.org/installer | php -- --version=1.8.4 --install-dir=/usr/local/bin --filename=composer \
        # Cleaning
        && apt-get purge -y --auto-remove $BUILD_DEPS \
        && apt-get autoremove -y \
        && rm -rf /var/lib/apt/lists/* \
        && chown www-data:www-data ${PHP_DATA_DIR} -Rf

EXPOSE 80 443

# Start apache.
CMD ["/usr/sbin/apache2ctl", "-DFOREGROUND"]
# Start cron
CMD ["cron", "-f"]
