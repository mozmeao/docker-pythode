# docker-pythode

A Debian Jessie base image with official latest NodeJS 6.10, Tini, and either Python 2.7 or 3.6.

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
