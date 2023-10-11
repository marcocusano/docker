![build](https://img.shields.io/badge/build-release-brightgreen.svg) ![php-version](https://img.shields.io/badge/version-1.0-blue.svg) ![author](https://img.shields.io/badge/author-Marco%20Cusano-blue.svg)

# Docker Quickstart
A bunch of [Docker](https://www.docker.com) quickstart [containers](https://www.docker.com/resources/what-container/) for PHP Web Developers, using [docker-compose](https://docs.docker.com/compose/).

## Standalone Quickstarts
By using a standalone you'll have a protected container not accessible from the other containers.\
Which means that you can build your Apache/NGINX application by starting that specific container only.

### Using `standalone-apache`
- Join the `./standalone-apache` dir;
- Run `docker-compose up`;
- Start coding in `./src` dir.

### Using `standalone-nginx`
- Join the `./standalone-nginx` dir;
- Run `docker-compose up`;
- Start coding in `./src/public`;

## Network Quickstarts
By using a networked container you'll be able to access other containers in order to use parts of it.\
Which means that if you run an Apache or NGINX container, you may start the `network-database` container too.

### Mandatory of `network-database`
- Join the `./network-database` dir;
- Run `docker-compose up`;
- Enjoy your database!

This Network has been setted as `"restart": "always"` in order to start your Database Network everytime you launch Docker.\
Also, can be used by any container you want, by adding the following code on bottom of your `docker-compose.yml` file:
```YAML
networks:
    database:
        external: true
        name: database
```
and this following code on your container service:
```YAML
your_service:
    networks:
        - database
```

### Using `network-apache`
- Join the `./network-apache` dir;
- Run `docker-compose up`;
- Make sure that `network-database` container is running;
- Start coding in `./src`.

### Using `network-nginx`
- Join the `./network-apache` dir;
- Run `docker-compose up`;
- Make sure that `network-database` container is running;
- Start coding in `./src/public`

## Database
By using a Networked or a Standalone container you can manage your database by using phpMyAdmin on `http://localhost:8080`, with the credentials `root:root`. Instead by using the credentials `dev:dev` you'll join just a `test` database. The database host is `mysql:3306`.\
Don't forget, in case of Networked container usage, make sure that `network-database` is running.

## .ENV
By editing any `.env` file inside a Networked or a Standalone container you can customize your own server, db and app configuration.

