# Specify Base
FROM ubuntu:20.04

# Set the working directory
WORKDIR /workspace

# install git
#RUN apt-get update
#RUN apt-get upgrade -y
RUN apt-get install -y git

# Go into main repository Directory
WORKDIR /workspace/zulip

# Conncet to remote upstream
RUN git remote add -f upstream https://github.com/zulip/zulip.git

# From inside a clone of zulip.git:
RUN ./tools/provision
RUN source /srv/zulip-py3-venv/bin/activate
RUN ./tools/run-dev  # starts the development server
