# docker-pythode

A Debian Jessie base image with official latest NodeJS 6.10, Tini, and either Python 2.7 or 3.6.

Usage:

```docker
FROM mozmeao/base:pythode-3.6-6.10

WORKDIR /app
COPY . /app

CMD ["run-app"]
```
