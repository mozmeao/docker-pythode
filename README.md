# docker-pythode

Based on the [official `python:2.7-slim` and `python:3.6-slim` images](https://hub.docker.com/_/python/) respectively,
then adds NodeJS 6.11 from the [official Dockerfile](https://github.com/nodejs/docker-node/blob/master/6.11/slim/Dockerfile),
[Tini](https://github.com/krallin/tini), and some useful env vars.

Also includes an apt helper script called `apt-install`. It is a simple wrapper around the best way to use
`apt-get install` within a Dockerfile. It will run an update, install, and clear the apt cache to keep image size small.


We also provide `mozmeao/base:python-2.7` and `mozmeao/base:python-3.6` that are just the official python-slim images with the
same env vars set and convenience features added.

## Usage

A `Dockerfile` like the following should work for your app if you have both NodeJS and Python requirements.

```docker
FROM mozmeao/base:pythode-3.6-6.11

RUN apt-install libpq-dev postgresql-client

WORKDIR /app
ENV NODE_ENV production

COPY ./package.json ./
RUN  install

COPY ./requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt

CMD ["bin/run-app"]
```

There is also a tag for a version with Python 2.7. You can view more info about the image at the [Docker Hub](https://hub.docker.com/r/mozmeao/base/).
