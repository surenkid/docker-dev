This is fork from helder/php-5.3, add these php extensions:

- mssql
- phpredis

Fix php-fpm listen address bug, it can be used in docker compose like this:

```
version: "3"
services:
  nginx:
    image: nginx:1.12-alpine
    container_name: surenkid-nginx
    ports:
      - "80:80"
    networks:
      - dockerinnernet
    depends_on:
      - "php"
    volumes:
      - ~/docker_data2/nginx:/etc/nginx/conf.d
      - ~/docker_data2/wwwroot:/var/www/html:ro

  php:
    image: surenkid/php53:latest
    container_name: surenkid-php
    ports:
      - "9000:9000"
    networks:
      - dockerinnernet
    volumes:
      - ~/docker_data2/wwwroot:/var/www/html

networks: 
  dockerinnernet:
```
