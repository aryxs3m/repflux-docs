# Configuration

The configuration can be done via an environment file (`.env`).  The sample environment file is located at
[`.env.example`](https://github.com/aryxs3m/repflux-app/blob/master/.env.example).

If you ever hosted a Laravel application, you are likely familiar [with this](https://laravel.com/docs/12.x/configuration#environment-configuration).

## System

| Parameter             | Description                                                                                                                    | Default            |
|-----------------------|--------------------------------------------------------------------------------------------------------------------------------|--------------------|
| `APP_ENV`             | The application environment. You should always use production.                                                                 | `production`       |
| `APP_KEY`             | The application encryption key. This will be set up automatically in the installation and you should never change it manually. |                    |
| `APP_DEBUG`           | Enable or disable debug mode. You should never enable this in production.                                                      | `false`            |
| `APP_URL`             | The application URL. Used for URL generation.                                                                                  | `http://localhost` |
| `APP_LOCALE`          | The default locale of the application.                                                                                         | `en`               |
| `APP_FALLBACK_LOCALE` | The fallback locale of the application.                                                                                        | `en`               |
| `APP_FAKER_LOCALE`    | The locale for the demo data generator.                                                                                        | `en_US`            |

## Database

Repflux currently supports MySQL/MariaDB databases. There are three other database drivers available in Laravel
(PostgreSQL, SQLite, SQL Server), but they are not tested and not officially supported. SQLite is 100% not supported.

You can configure the database connection with the following parameters:

| Parameter       | Description                                           | Default    |
|-----------------|-------------------------------------------------------|------------|
| `DB_CONNECTION` | The database driver: mysql, mariadb, pgsql or sqlsrv. | `mysql`    |
| `DB_HOST`       | Database server hostname or IP.                       | `mysql`    |
| `DB_PORT`       | Database server port.                                 | `3306`     |
| `DB_DATABASE`   | Database name.                                        | `laravel`  |
| `DB_USERNAME`   | Database username.                                    | `sail`     |
| `DB_PASSWORD`   | Database password.                                    | `password` |

## Email

Repflux can send emails for account verification, password reset and reminders. Laravel supports several mail drivers
out of the box, but Repflux only support SMTP or sendmail. You can configure the email settings with the following
parameters:

| Parameter           | Description                                    | Default            |
|---------------------|------------------------------------------------|--------------------|
| `MAIL_MAILER`       | The mailer to use: smtp, sendmail, log, array. | `smtp`             |
| `MAIL_HOST`         | The SMTP server hostname or IP.                | `mailpit`          |
| `MAIL_PORT`         | The SMTP server port.                          | `1025`             |
| `MAIL_USERNAME`     | The SMTP username.                             |                    |
| `MAIL_PASSWORD`     | The SMTP password.                             |                    |
| `MAIL_ENCRYPTION`   | The encryption to use: tls, ssl or null.       | `null`             |
| `MAIL_FROM_ADDRESS` | The email address to use in the "from" field.  | `info@repflux.app` |
| `MAIL_FROM_NAME`    | The name to use in the "from" field.           | `Repflux`          |

## Redis

Repflux uses Redis for caching and session management. You can configure the Redis connection with the following:

| Parameter        | Description                  | Default    |
|------------------|------------------------------|------------|
| `REDIS_CLIENT`   | Redis client.                | `phpredis` |
| `REDIS_HOST`     | Redis server hostname or IP. | `redis`    |
| `REDIS_PASSWORD` | Redis server password        |            |
| `REDIS_PORT`     | Redis server port            |            |

## Demo

Repflux has a demo mode, which can be enabled with the following parameters:

| Parameter           | Description                                                                | Default            |
|---------------------|----------------------------------------------------------------------------|--------------------|
| `APP_DEMO`          | Enable or disable demo mode.                                               | `false`            |
| `APP_DEMO_EMAIL`    | The email address of the demo user.                                        | `demo@repflux.app` |
| `APP_DEMO_PASSWORD` | The password of the demo user. Can be anything, as long as it's not empty. | `Repflux12345678`  |

## OAuth Providers

Several OAuth providers are supported for authentication. If you leave them empty, they will be disabled. You can
configure them with the following parameters:

| Parameter                | Description                   | Default |
|--------------------------|-------------------------------|---------|
| `GITHUB_CLIENT_ID`       | GitHub OAuth client ID.       |         |
| `GITHUB_CLIENT_SECRET`   | GitHub OAuth client secret.   |         |
| `GOOGLE_CLIENT_ID`       | Google OAuth client ID.       |         |
| `GOOGLE_CLIENT_SECRET`   | Google OAuth client secret.   |         |
| `DISCORD_CLIENT_ID`      | Discord OAuth client ID.      |         |
| `DISCORD_CLIENT_SECRET`  | Discord OAuth client secret.  |         |
| `FACEBOOK_CLIENT_ID`     | Facebook OAuth client ID.     |         |
| `FACEBOOK_CLIENT_SECRET` | Facebook OAuth client secret. |         |
