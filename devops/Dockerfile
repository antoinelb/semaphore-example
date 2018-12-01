# vim: ft=dockerfile:
from alpine:latest

run mkdir /app
workdir /app

run apk update && \
    apk add --no-cache python3 \
                       libffi \
                       openssl \
                       python3-dev \
                       build-base \
                       libffi-dev \
                       openssl-dev \
                       curl

run pip3 install --upgrade pip; \
    pip3 install poetry

run python3 -m venv venv; \
    . venv/bin/activate

copy ./pyproject.* /app/
run poetry install

run apk del python3-dev \
            build-base \
            libffi-dev \
            openssl-dev \
            curl

copy . /app
