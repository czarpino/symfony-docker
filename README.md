# Supported tags and respective Dockerfile links

- [`4.1`, `latest` *(4.1/Dockerfile)*](https://github.com/czarpino/symfony-docker/blob/ffea920d1955522035345d36b9e8d087bc66c89a/4.1/Dockerfile)

# What is Symfony?

The leading PHP framework to create websites and web applications. Built on top of the Symfony Components.

> http://symfony.com/what-is-symfony

# How to use this image.

```
version: '3'
services:
    app:
        image: czarpino/symfony:4.1
        volumes:
            - ./:/var/www/project
    server:
        image: nginx:1.15-alpine
        volumes:
            - ./etc/nginx/template.nginx.conf:/etc/nginx/conf.d/template.nginx
        ports:
            - "80:80"
        environment:
            - NGINX_HOST=example.com
            - NGINX_PORT=80
        command: /bin/sh -c "envsubst '$$NGINX_HOST $$NGINX_PORT' < /etc/nginx/conf.d/template.nginx > /etc/nginx/conf.d/default.conf && exec nginx -g 'daemon off;'"
```

See [Configuring a Web Server (Symfony Docs)](https://symfony.com/doc/current/setup/web_server_configuration.html#nginx) on how to configure Nginx in front of PHP-FPM.