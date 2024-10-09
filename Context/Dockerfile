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
ARG checkoutName=4e29d691637197c3900bc55c54d5af211896e1ef
RUN git clone https://github.com/VCityTeam/TunNetView.git
WORKDIR TunNetView
RUN git checkout $checkoutName
RUN npm install
RUN npm run build

### Service the client code
CMD [ "npm", "run", "start" ]
