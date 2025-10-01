# Native

## System requirements

- supported Linux OS (e.g. Ubuntu 24.04, Debian 12)
- PHP 8.4 CLI and FPM
- PHP extensions: pdo, mysql, intl, curl, redis
- MySQL / MariaDB
- Redis
- nginx
- composer
- NodeJS
- npm

## Installation

### Application installation

Check out the project in your www/vhost root, make sure the web server can access it:

```shell
git clone https://github.com/aryxs3m/repflux-app.git /var/www/repflux
chown -R www-data:www-data /var/www/repflux
cd /var/www/repflux
```

Allow write permission to these folders:

```shell
chmod -R +w storage
chmod -R +w bootstrap 
```

Copy the sample .env file, adjust the parameters:

```shell
cp .env.example .env
```

Install packages, build assets:

```shell
npm i
npm run build
composer install --no-dev --optimize-autoloader
```

Finish installation:

```shell
php artisan key:gen
php artisan migrate
php artisan optimize
php artisan filament:optimize
```

### nginx configuration

Create a new configuration:

```shell
touch /etc/nginx/sites-available/repflux
```

Use this as a template:

```
server {
    listen 80;
    listen [::]:80;

    server_name repflux.yourdomain.com;
    root /var/www/repflux/public;

    add_header X-Frame-Options "SAMEORIGIN";
    add_header X-Content-Type-Options "nosniff";

    index index.php index.html;

    charset utf-8;

    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }

    location = /favicon.ico   { access_log off; log_not_found off; }
    location = /manifest.json { access_log off; log_not_found off; }
    location = /robots.txt    { access_log off; log_not_found off; }

    error_page 404 /index.php;

    location ~ \.php$ {
        fastcgi_pass unix:/var/run/php/php8.4-fpm.sock;
        fastcgi_param SCRIPT_FILENAME $realpath_root$fastcgi_script_name;
        fastcgi_param PHP_VALUE open_basedir="/var/www/repflux:/tmp";
        include fastcgi_params;
    }

    location ~ /\.(?!well-known).* {
        deny all;
    }

    access_log /var/log/nginx/repflux-access;
    error_log  /var/log/nginx/repflux-error;
}
```

Modify **repflux.yourdomain.com** to your domain and **/var/www/repflux** to the directory you used to check out the
project.

Enable, test and apply the configuration:

```shell
ln -s /etc/nginx/sites-available/repflux /etc/nginx/sites-enabled/repflux
nginx -t
systemctl reload nginx
```

## Upgrading

You need to pull the changes, reinstall and regenerate assets and drop the cached components/settings:

```shell
git pull
npm i
npm run build
composer install --no-dev --optimize-autoloader
php artisan migrate
php artisan optimize
php artisan filament:optimize
```
