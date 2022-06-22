FROM php:8.1-fpm-buster
WORKDIR "/app"

# web
# https://hub.docker.com/r/phpswoole/swoole

RUN sed -i "s/deb.debian.org/mirrors.aliyun.com/g" /etc/apt/sources.list

#编译安装核心扩展 gd
RUN apt-get update -y && \
    apt-get install git -y

RUN apt-get install inotify-tools -y
RUN apt-get install vim -y
RUN apt-get install net-tools -y
#RUN apt-get install nodejs -y

# Install selected extensions
RUN apt-get update -y && \
    apt-get install -y  --no-install-recommends libpq-dev \
    libmagickcore-dev \
    libmagickwand-dev \
    imagemagick \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libmcrypt-dev \
    libpng-dev \
    libonig-dev \
    libzip-dev \
    libxslt1-dev

RUN docker-php-ext-install \
    pdo \
    -j$(nproc) gd iconv  pdo_mysql mbstring zip exif pcntl bcmath soap opcache xsl \
    && pecl channel-update pecl.php.net \
    && pecl install redis-5.3.7 \
    && pecl install imagick \
#    && pecl install inotify \
#    && pecl install mcrypt \
    && pecl install xdebug \
    && docker-php-ext-enable redis imagick opcache

RUN mv $PHP_INI_DIR/php.ini-production $PHP_INI_DIR/php.ini

COPY /init.sh /init.sh
RUN chmod +x /init.sh

#COPY --chown=www-data:www-data . ~/app/

#COPY  ../../app/new_crm new_crm/
#
#RUN chown -R www-data:www-data /app/new_crm/storage/