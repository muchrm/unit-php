FROM php:7.2-fpm-stretch
LABEL maintainer="muchrm.me@gmail.com"
RUN rm /etc/apt/preferences.d/no-debian-php && apt-get update && apt-get install -y --no-install-recommends\
                gnupg \
                apt-transport-https \
                ca-certificates \
                curl \
                php-dev \
                libphp-embed \
                && rm -rf /var/lib/apt/lists/*

RUN curl -O https://nginx.org/keys/nginx_signing.key
RUN apt-key add nginx_signing.key

ADD unit.list  /etc/apt/sources.list.d

RUN apt-get update && apt-get install  --no-install-recommends  -y unit unit-php && rm -rf /var/lib/apt/lists/*

CMD ["unitd","--no-daemon","--control","0.0.0.0:8000"]