# Supported tags and respective Dockerfile links

- [`4.1`, `latest` *(4.1/Dockerfile)*](https://github.com/czarpino/symfony-docker/blob/ffea920d1955522035345d36b9e8d087bc66c89a/4.1/Dockerfile)

# What is Symfony?

The leading PHP framework to create websites and web applications. Built on top of the Symfony Components.

> http://symfony.com/what-is-symfony

# How to use this image.

Get image with a docker pull

```
docker pull czarpino/symfony
```

Alternatively, you can use this image for your docker-compose file:

```
version: '3'
services:
    app:
        image: czarpino/symfony:4.1
        volumes:
            - ./:/var/www/project
```