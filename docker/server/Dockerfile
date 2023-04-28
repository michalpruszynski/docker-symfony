FROM php:8.1-apache

RUN docker-php-ext-install mysqli && docker-php-ext-enable mysqli && docker-php-ext-install pdo_mysql
RUN a2enmod rewrite && a2enmod ssl && a2enmod socache_shmcb
RUN sed -i '/SSLCertificateFile.*snakeoil\.pem/c\SSLCertificateFile \/etc\/ssl\/certs\/mycert.crt' /etc/apache2/sites-available/default-ssl.conf && sed -i '/SSLCertificateKeyFile.*snakeoil\.key/cSSLCertificateKeyFile /etc/ssl/private/mycert.key\' /etc/apache2/sites-available/default-ssl.conf
RUN a2ensite default-ssl
RUN apt-get update && apt-get upgrade -y 
RUN apt-get install -y zlib1g-dev libicu-dev g++
RUN docker-php-ext-configure intl
RUN docker-php-ext-install intl
 
# Installes the mySQL client library pdo_mysql.
# RUN docker-php-ext-install pdo_mysql 
# RUN a2enmod ssl && a2enmod socache_shmcb

# Uncomment if you require the gd php extension
RUN apt-get install -y libfreetype6-dev libjpeg62-turbo-dev && \
    docker-php-ext-configure gd  && \
    docker-php-ext-install gd

# Uncomment if you require opcache
RUN docker-php-ext-install opcache  

RUN apt-get install -y \
        libzip-dev \
        zip \
  && docker-php-ext-install zip
  
# Uncomment if you requrie apache rewrite mod.
RUN a2enmod rewrite

# RUN mkdir -p /var/www/html/public/pdf
# RUN chmod -R 775 /var/www/html/public/pdf

# Uncomment to enable xdebug
# RUN pecl install xdebug-beta &&\
#     docker-php-ext-enable xdebug &&\
#     echo "xdebug.remote_enable=on" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini &&\
#     echo "xdebug.remote_autostart=on" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini &&\
#     echo "xdebug.remote_connect_back=off" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini &&\
#     echo "xdebug.remote_handler=dbgp" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini &&\
#     echo "xdebug.profiler_enable=0" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini &&\
#     echo "xdebug.profiler_output_dir=\"/var/www/html\"" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini &&\
#     echo "xdebug.remote_port=9000" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini &&\
#     echo "xdebug.remote_host = host.docker.internal" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini

RUN apt-get clean