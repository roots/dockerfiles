FROM ubuntu:18.04
RUN rm /bin/sh && ln -s /bin/bash /bin/sh

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update
RUN apt-get install -y software-properties-common
RUN add-apt-repository ppa:ondrej/php
RUN apt-get update
RUN apt-get install -yq --no-install-recommends \
    curl \
    zip \
    # Install PHP 7.1
    php7.1-cli \
    php7.1-common \
    php7.1-curl \
    php7.1-dev \
    php7.1-fpm \
    php7.1-gd \
    php7.1-mbstring \
    php7.1-mysql \
    php7.1-opcache \
    php7.1-xml \
    php7.1-xmlrpc \
    php7.1-zip

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Install nvm, Yarn
ENV NVM_DIR /usr/local/nvm
ENV NODE_VERSION 10.15.3

RUN apt-get -y install curl
RUN mkdir /usr/local/nvm && curl https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash
RUN source $NVM_DIR/nvm.sh && nvm install $NODE_VERSION && nvm alias default $NODE_VERSION && nvm use default

ENV NODE_PATH $NVM_DIR/v$NODE_VERSION/lib/node_modules
ENV PATH      $NVM_DIR/versions/node/v$NODE_VERSION/bin:$PATH

RUN npm install -g yarn
