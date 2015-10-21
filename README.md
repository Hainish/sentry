# Sentry Docker-Compose

This provides an easy way to bootstrap the [Sentry](https://getsentry.com/) docker infrastructure.  You'll need `docker` and `docker-compose` to use this.

## Setup

    docker-compose up
    docker run -it --rm --link sentry_postgres_1:postgres --link sentry_redis_1:redis sentry sentry upgrade

Next, you'll have to edit the settings in `sentry.conf.py` like so:

    vim `docker inspect -f '{{ index .Volumes "/home/user/.sentry" }}' sentry_sentry_1`/sentry.conf.py

Change the config options for any settings you want to customize, then:

    docker-compose stop

## Running

From now on, you just run

    docker-compose up

to start.  Direct your browser to [https://localhost:8080/](https://localhost:8080/) to view the Sentry UI.  To stop, run

    docker-compose stop
