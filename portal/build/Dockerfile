FROM php:8.1.2-fpm

WORKDIR /var/www/portal

# install linux packages
RUN apt-get update && apt-get install -y \
    git \
    zip \
    unzip

# install composer
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php -r "if (hash_file('sha384', 'composer-setup.php') === '55ce33d7678c5a611085589f1f3ddf8b3c52d662cd01d4ba75c0ee0459970c2200a51f492d557530c71c15d8dba01eae') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
RUN php composer-setup.php
RUN chmod +x composer.phar
RUN mv composer.phar /usr/local/bin/composer
RUN php -r "unlink('composer-setup.php');"

# install infection
RUN php -r "copy('https://github.com/infection/infection/releases/download/0.26.15/infection.phar', 'infection.phar');"
RUN chmod +x infection.phar
RUN mv infection.phar /usr/local/bin/infection

# install psalm
RUN php -r "copy('https://github.com/vimeo/psalm/releases/latest/download/psalm.phar', 'psalm.phar');"
RUN chmod +x psalm.phar
RUN mv psalm.phar /usr/local/bin/psalm

RUN cp /usr/local/etc/php/php.ini-production /usr/local/etc/php/php.ini &&  \
    sed -i -e "s/^ *memory_limit.*/memory_limit = 4G/g" /usr/local/etc/php/php.ini