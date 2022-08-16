FROM litespeedtech/openlitespeed:1.6.9-lsphp74
#MAINTAINER Riki Permana <rikipermana@live.com>
RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
    apt-utils \
 && rm -rf /var/lib/apt/lists/*
RUN add-apt-repository ppa:ondrej/php
RUN apt-get update && apt-get upgrade -y
RUN apt-get install software-properties-common -y
RUN apt-get install -y php7.4 php7.4-mbstring php7.4-pgsql php7.4-curl php7.4-zip php7.4-bz2
RUN update-alternatives --set php /usr/bin/php7.4
RUN add-apt-repository 'deb http://rpms.litespeedtech.com/debian/ bionic main'
RUN apt-get install nano git lsphp74-pgsql composer -y
RUN /usr/local/lsws/admin/misc/admpass.sh
RUN ssh-keygen -t rsa
COPY ./src /var/www/vhosts/localhost/html
