FROM alpine:3.6
MAINTAINER Aris Prawisudatama <soedomoto@gmail.com>

RUN apk upgrade --update

# Install essential
RUN apk add --no-cache alpine-sdk python3 python3-dev openssl openssl-dev

# FROM ubuntu:xenial
# MAINTAINER "Soedomoto <soedomoto@gmail.com>"
#
# ## Base
# ## --
# RUN apt-get update
# RUN apt-get install --no-install-recommends -y\
#  python python-pip
# RUN apt-get clean
#
## Install requirement
## --
RUN pip3 install --upgrade --no-cache-dir pip setuptools
RUN pip3 install --no-cache-dir consulate flask grpcio grpcio-tools

RUN apk del alpine-sdk python3-dev

RUN mkdir -p /app
COPY . /app

EXPOSE 80
