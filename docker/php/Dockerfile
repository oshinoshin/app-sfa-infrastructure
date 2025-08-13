ARG PHP_VERSION

FROM php:${PHP_VERSION}

# 必要なシステムパッケージと PHP 拡張をインストール
RUN apt-get update && apt-get install -y \
    git \
    unzip \
    zip \
    libpng-dev \
    libonig-dev \
    libxml2-dev \
    libzip-dev \
    curl \
    && docker-php-ext-install pdo_mysql mbstring exif pcntl bcmath gd zip \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

# Composer インストール（公式推奨方法）
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

# 作業ディレクトリ設定（Laravel のルート）
WORKDIR /var/www/html

# アプリ全体をコピー
COPY app-sfa-backend .

# 依存関係インストール（vendor 作成）
RUN composer install

# オートローダー最適化
RUN composer dump-autoload --optimize

# 権限設定（www-data は PHP-FPM の実行ユーザー）
RUN chown -R www-data:www-data /var/www/html \
    && chmod -R 775 /var/www/html/storage /var/www/html/bootstrap/cache

# ポート 9000 を PHP-FPM で待受
EXPOSE 9000

# PHP-FPM 起動
CMD ["php-fpm"]