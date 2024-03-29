FROM nvidia/cuda:11.1-base-ubuntu18.04

# set work directory
WORKDIR /usr/src/app

ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# change ubuntu download server from default to kakao of korea
RUN cd /etc/apt && sed -i 's/archive.ubuntu.com/mirror.kakao.com/g' sources.list
    # sed -i 's/archive.ubuntu.com/mirror.kakao.com/g' sources.list.d/proposed.list

RUN cd /usr/src/app

RUN apt-get update -y

# install necessary libraries
RUN apt-get install -y build-essential gcc git netcat

# install pip, python
RUN apt-get install -y python3-pip python3-dev

# install postgreSQL
RUN apt-get install -y python-psycopg2

# solve cv2 error
RUN apt-get install -y libgl1-mesa-glx

# install dependencies
RUN python3 -m pip install --upgrade pip
COPY requirements .
RUN python3 -m pip install -r development.txt

# install mit-semseg library
RUN pip install git+https://github.com/CSAILVision/semantic-segmentation-pytorch.git@master

# copy entrypoint.sh
COPY ./entrypoint.sh .

# copy project
COPY . .

# run entrypoint.sh
ENTRYPOINT ["/usr/src/app/entrypoint.sh"]

CMD ["gunicorn", "--bind", ":8000", "--workers", "3", "config.wsgi:application"]