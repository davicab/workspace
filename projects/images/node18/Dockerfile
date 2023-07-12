FROM ubuntu:22.04

ARG USER_ID
ARG GROUP_ID

RUN apt-get update && \
    apt-get install -y tzdata && \
    echo date && \
    apt-get install -y sudo && \ 
    sudo apt-get install -y curl && \
    curl -sL https://deb.nodesource.com/setup_18.x | sudo -E bash - && \
    sudo apt-get install -y nodejs && \
    sudo apt-get install -y autoconf libtool pkg-config nasm build-essential

RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add - && \
    echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list && \
    apt update && sudo apt install -y yarn

RUN npm install --global gulp-cli

RUN addgroup --gid $GROUP_ID user
RUN adduser --disabled-password --gecos '' --uid $USER_ID --gid $GROUP_ID user
USER user
