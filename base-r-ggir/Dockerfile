## Base image: https://hub.docker.com/u/rocker/
FROM rocker/r-base:latest

## copy files
COPY /code/install_packages.R /install_packages.R


# Install prerequisites
RUN apt-get update && apt-get install -y \
libcurl4-openssl-dev libssl-dev libcurl4-doc \
libidn11-dev libkrb5-dev libldap2-dev \
librtmp-dev libssh2-1-dev libssl-dev libxml2-dev
CMD /bin/bash

## install R packages
RUN Rscript /install_packages.R
