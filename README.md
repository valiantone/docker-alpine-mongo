# docker-alpine-mongo

This repository contains Dockerfile for [MongoDB 3.4.10](https://www.mongodb.org)
container, based on the [Alpine edge](https://hub.docker.com/_/alpine/) image.

Why ? the official mongo image size: 360 MB, alpine-mongo: 106 MB

## Install

As a prerequisite, you need [Docker](https://docker.com) to be installed.

To download this image from the public docker hub:

	$ docker pull valiantone/alpine-mongo

To re-build this image from the dockerfile:

	$ docker build -t valiantone/alpine-mongo .

## Usage

To run `mongod`:

	$ docker run -d --name mongo -p 27017:27017 valiantone/alpine-mongo

You can also specify the database repository where to store the data
with the volume -v option:

    $ docker run -d --name mongo -p 27017:27017 \
	  -v /somewhere/onmyhost/mydatabase:/data/db \
	  valiantone/alpine-mongo

To run a shell session:

    $ docker exec -ti mongo sh

To use the mongo shell client:

	$ docker exec -ti mongo mongo

The mongo shell client can also be run its own container:

	$ docker run -ti --rm --name mongoshell mongo host:port/db

## Limitations

- On MacOSX, volumes located in a virtualbox shared folder are not
  supported, due to a limitation of virtualbox (default docker-machine
  driver) not supporting fsync().
