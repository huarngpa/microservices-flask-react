# base image
from node:11.12.0-alpine

# set working directory
workdir /app/client

# add `/usr/src/app/node_modules/.bin` to $PATH
env PATH /app/client/node_modules/.bin:$PATH

# install and cache app dependencies
copy package.json /app/client/package.json
copy package-lock.json /app/client/package-lock.json
run npm ci
run npm install react-scripts@2.1.8 -g --silent

# start app
cmd ["npm", "start"]
