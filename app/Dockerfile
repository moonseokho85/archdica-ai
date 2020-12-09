FROM nvidia/cuda:11.1.0-devel-ubuntu18.04

LABEL maintainer="mseokho7733@gmail.com"

# set work directory
WORKDIR /usr/src/app

ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

RUN apt-get update -y
RUN apt-get install -y python3 python3-pip python3-dev build-essential

# install dependencies
RUN pip install --upgrade pip
COPY requirements.txt .
RUN pip install -r requirements.txt

# copy project
COPY . .