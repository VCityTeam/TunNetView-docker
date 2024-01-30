FROM ubuntu:jammy

LABEL maintainer "VCityTeam"
LABEL source.repo "https://github.com/VCityTeam/TunNetView-docker"

# Install system dependencies
RUN apt-get update

# Node version 18 is required. For its installation (on jammy) refer to e.g.
# https://linux.how2shout.com/3-ways-to-install-nodejs-npm-on-ubuntu-22-04-lts-jammy/
RUN apt-get install -y curl
RUN curl -sL https://deb.nodesource.com/setup_18.x | bash -
RUN apt-get install -y nodejs
# For the record
RUN node --version
RUN npm --version
RUN apt-get install -y git
RUN git --version

######### Install TunNetView
ARG checkoutName=cc7b1c9c65b0708c46a3292c07f93c265de5d347
RUN git clone https://github.com/VCityTeam/TunNetView.git
WORKDIR TunNetView
RUN git checkout $checkoutName
RUN npm install
RUN npx webpack --config webpack.config.js

### Service the client code
RUN npm install http-server -g

CMD [ "http-server", "-p", "8080" ]
