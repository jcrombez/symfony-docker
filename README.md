![symfony-docker](http://i.imgur.com/vc5ZVqL.png?2)

# Symfony + Nginx + php-fpm
[![Foo](https://badge.imagelayers.io/kitpages/symfony:7.0.svg)](https://imagelayers.io/?images=kitpages/symfony:7.0)

Docker for Symfony application, powered by **Nginx** and **php-fpm**.

Based on Debian Jessie.

If you are experiencing some issues, take a look at [TROUBLESHOOTING](TROUBLESHOOTING.md)

## Usage

```bash
docker pull kitpages/symfony:7.0
```

Then run in your symfony folder

```bash
docker run -v $(pwd):/var/www -p 8080:80 kitpages/symfony:7.0
```

Symfony app will be accessible on http://localhost:8080/app.php

## Custom nginx configuration

If you want to replace the default nginx settings, overwrite configuration file at `/etc/nginx/sites-enabled/default`. 

```dockerfile
COPY nginx.conf /etc/nginx/sites-enabled/default
```

You may also want to add only some directives in [existing site config](config/vhost.conf#L5).

```dockerfile
COPY custom-config.conf /etc/nginx/conf.d/docker/custom-config.conf 
```

## Minimal package included

* nginx
* php7.0-fpm
* php7.0-cli
* php7.0-intl

## Exposed port
* 80 : nginx
