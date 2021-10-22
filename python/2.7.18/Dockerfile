FROM python:2.7.18-slim

RUN apt update && apt install -y --no-install-recommends bzip2 g++ curl

ARG PYPY_TAR_FILE=https://downloads.python.org/pypy/pypy2.7-v7.3.5-linux64.tar.bz2

RUN curl ${PYPY_TAR_FILE} -o /tmp/pypy.tar.bz2

RUN mkdir /opt/pypy

RUN tar -xjC /opt/pypy --strip-components=1 -f /tmp/pypy.tar.bz2

RUN rm /tmp/pypy.tar.bz2

RUN ln -sv /opt/pypy/bin/pypy /usr/local/bin/pypy

WORKDIR /opt/code
