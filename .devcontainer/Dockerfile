FROM ubuntu:20.04

USER root

# Set environment variables for non-interactive installation
ENV DEBIAN_FRONTEND=noninteractive

# Install required packages for locale, SQL Server tools, and dependencies
RUN apt-get update && \
    apt-get install -y locales git curl wget software-properties-common apt-transport-https && \
    echo "en_US.UTF-8 UTF-8" > /etc/locale.gen && \
    locale-gen en_US.UTF-8 && \
    update-locale LANG=en_US.UTF-8 && \
    export LANG=en_US.UTF-8 && \
    export LANGUAGE=en_US:en && \
    export LC_ALL=en_US.UTF-8

# Set environment variables for the locale and language
ENV LANG=en_US.UTF-8 \
    LANGUAGE=en_US:en \
    LC_ALL=en_US.UTF-8

RUN apt-get update && apt-get install -y git curl wget software-properties-common 

RUN curl https://packages.microsoft.com/keys/microsoft.asc | tee /etc/apt/trusted.gpg.d/microsoft.asc
    
RUN add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/20.04/prod.list)"

RUN apt-get update && apt-get install -y sqlcmd

