FROM ubuntu:bionic
MAINTAINER rikipermana <rikipermana@live.com>

ENV OS_LOCALE="en_US.UTF-8"
RUN apt-get update && apt-get install -y locales && locale-gen ${OS_LOCALE}
ENV LANG=${OS_LOCALE} \
    LANGUAGE=${OS_LOCALE} \
    LC_ALL=${OS_LOCALE} \
    DEBIAN_FRONTEND=noninteractive

RUN     \
        BUILD_DEPS='software-properties-common' \
    && dpkg-reconfigure locales \
        && apt-get install --no-install-recommends -y $BUILD_DEPS \
		&& apt-get install --no-install-recommends -y $BUILD_DEPS \
        && add-apt-repository -y ppa:ondrej/apache2 \
		&& add-apt-repository universe \
		&& add-apt-repository ppa:certbot/certbot \
        && apt-get update \
    && apt-get install -y software-properties-common curl apache2 nano cron certbot python-certbot-apache openssh-server \
        # Cleaning
        && apt-get purge -y --auto-remove $BUILD_DEPS \
        && apt-get autoremove -y \
        && rm -rf /var/lib/apt/lists/*
RUN a2enmod proxy
RUN a2enmod proxy_http
RUN a2enmod headers
EXPOSE 80 443

# By default, simply start apache.
CMD ["/usr/sbin/apache2ctl", "-DFOREGROUND"]
