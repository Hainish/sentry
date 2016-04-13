# Sentry Docker-Compose

This provides an easy way to bootstrap the [Sentry](https://getsentry.com/) docker infrastructure.  You'll need `docker` and `docker-compose` to use this.

## Setup

    cp docker-compose.yml.example docker-compose.yml
    docker-compose up -d postgres redis
    docker run --rm sentry generate-secret-key

With the key generated above, run:

    docker run -it --rm -e SENTRY_SECRET_KEY='<secret-key>' --link sentry_postgres_1:postgres --link sentry_redis_1:redis sentry upgrade

Add the key to `SENTRY_SECRET_KEY` in `docker-compose.yml` in three places, and change any mail settings in this file.  Then:

    docker-compose up

## Running

From now on, you just run

    docker-compose up

to start.  Direct your browser to [https://localhost:8080/](https://localhost:8080/) to view the Sentry UI.  To stop, run

    docker-compose stop
