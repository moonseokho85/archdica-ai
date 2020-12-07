FROM ubuntu:18.04

LABEL maintainer="mseokho7733@gmail.com"

ENV PYTHONUNBUFFERED 1

RUN apt-get update -y
RUN apt-get install -y python3 python3-pip python3-dev build-essential

RUN mkdir /code
WORKDIR /code

ADD requirements.txt /code/
RUN pip install -r requirements.txt

ADD . /code/