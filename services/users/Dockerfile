# base image
from python:3.7.2-slim

# install dependencies
run apt-get update && \
    apt-get -y install netcat && \
    apt-get clean

# set working directory
workdir /usr/src/app

# add and install requirements
copy ./requirements.txt /usr/src/app/requirements.txt
run pip install -r requirements.txt

# add entrypoint.sh
copy ./entrypoint.sh /usr/src/app/entrypoint.sh
run chmod +x /usr/src/app/entrypoint.sh

# add app
copy . /usr/src/app

# run server
cmd ["/usr/src/app/entrypoint.sh"]
