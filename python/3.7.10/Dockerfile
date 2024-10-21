FROM python:3.13-slim

RUN apt update && apt install -y --no-install-recommends bzip2 g++ curl

ARG PYPY_TAR_FILE=https://downloads.python.org/pypy/pypy3.7-v7.3.5-linux64.tar.bz2

RUN curl ${PYPY_TAR_FILE} -o /tmp/pypy3.tar.bz2

RUN mkdir /opt/pypy

RUN tar -xjC /opt/pypy --strip-components=1 -f /tmp/pypy3.tar.bz2

RUN rm /tmp/pypy3.tar.bz2

RUN ln -sv /opt/pypy/bin/pypy3 /usr/local/bin/pypy3

WORKDIR /opt/code
