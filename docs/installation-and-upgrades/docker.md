# Docker Compose

You can run a production ready Repflux instance in seconds using Docker Compose.

## Installation

Check out the project from GitHub:

```shell
git clone https://github.com/aryxs3m/repflux-app.git
cd repflux-app
```

Copy the sample environment settings, modify them if needed:

```shell
cp .env.example .env
```

Start the containers:

```shell
docker-compose --file docker-compose.nginx.yaml --env-file=.env up -d
```

## Upgrade

Stop the containers, update the project, restart the containers:

```shell
docker-compose down
git pull
docker-compose --file docker-compose.nginx.yaml --env-file=.env up -d
```

Any necessary migration or script will be run after startup.
