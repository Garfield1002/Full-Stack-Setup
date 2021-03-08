FROM python:3.9-slim-buster
# I should use  ubuntu:20.04

# set work directory
WORKDIR /usr/src/app

# set environment variables
ENV PYTHONUNBUFFERED 1

RUN apt-get update && apt-get install -y\
    # required for uwsgi
    python-dev \
    build-essential

# install pipenv
RUN pip install --upgrade pip
RUN pip install pipenv

# install python dependencies
COPY ./Pipfile .
COPY ./Pipfile.lock .
RUN pipenv install

# install uwsgi
RUN pipenv install uwsgi


# copy project
COPY . .