# Specify Base
FROM ubuntu:20.04

# Set the working directory
WORKDIR /workspace

# install git
RUN apt-get update
RUN apt-get upgrade -y
RUN apt-get install -y git

# Go into main repository Directory
WORKDIR /workspace/zulip

# Initialize git repository
RUN git init
# Conncet to remote upstream
RUN git remote add -f upstream https://github.com/zulip/zulip.git

# Copy files from reposity to Docker:
COPY ./tools/provision /tools/provision
COPY ./tools/run-dev /tools/run-dev

# Create non-root user to run scripts:
RUN useradd Zulip_User
USER Zulip_User

# Run Scripts
RUN bash /tools/provision
RUN source /srv/zulip-py3-venv/bin/activate 
# Start the development server
RUN bash /tools/run-dev  

