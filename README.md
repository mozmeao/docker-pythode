# docker-pythode

Based on the [official `python:2.7-slim` and `python:3.6-slim` images](https://hub.docker.com/_/python/) respectively,
then adds NodeJS 6.10 from the [official Dockerfile](https://github.com/nodejs/docker-node/blob/master/6.10/Dockerfile),
[Tini](https://github.com/krallin/tini), and some useful env vars.


## Usage

A `Dockerfile` like the following should work for your app if you have both NodeJS and Python requirements.

```docker
FROM mozmeao/base:pythode-3.6-6.10

WORKDIR /app
ENV NODE_ENV production

COPY ./package.json ./
RUN npm install

COPY ./requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt

CMD ["bin/run-app"]
```

There is also a tag for a version with Python 2.7. You can view more info about the image at the [Docker Hub](https://hub.docker.com/r/mozmeao/base/).
