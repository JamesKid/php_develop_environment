FROM phpswoole/swoole:4.8.8-php8.1
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
RUN apt-get install nodejs -y

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
#    -j$(nproc) gd iconv  pdo_mysql mbstring zip exif pcntl bcmath soap opcache xsl \
    -j$(nproc) gd iconv  pdo_mysql mbstring zip exif pcntl bcmath soap xsl \
    && pecl channel-update pecl.php.net \
    && pecl install redis-5.3.7 \
    && pecl install imagick \
#    && pecl install inotify \
#    && pecl install mcrypt \
#    && pecl install xdebug \
#    && docker-php-ext-enable redis imagick inotify
    && docker-php-ext-enable redis imagick