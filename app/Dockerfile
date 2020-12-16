FROM nvidia/cuda:11.1-devel-ubuntu18.04

LABEL maintainer="mseokho7733@gmail.com"

# set work directory
WORKDIR /usr/src/app

ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

RUN apt-get update -y
RUN apt-get install -y python3 python3-pip python3-dev build-essential

# install dependencies
RUN python3 -m pip install --upgrade pip
COPY requirements .
RUN pwd
RUN ls -al
RUN python3 -m pip install -r requirements/promotion.txt

# copy project
COPY . .