FROM php:8.2-fpm

# php.ini の設定をコンテナ内にコピー
COPY php.ini /usr/local/etc/php/

# 必要なパッケージをインストール
RUN apt update \
    && apt install -y default-mysql-client zlib1g-dev libzip-dev unzip \
    && docker-php-ext-install pdo_mysql zip

# Composer のインストール
RUN curl -sS https://getcomposer.org/installer | php \
    && mv composer.phar /usr/local/bin/composer \
    && composer self-update

# ユーザーの追加
RUN useradd -m root_user

# GDライブラリのインストール
RUN apt-get update \
    && apt-get install -y \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install gd

# 作業ディレクトリを設定
WORKDIR /var/www
