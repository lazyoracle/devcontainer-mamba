FROM docker.io/condaforge/mambaforge:latest

# FROM --platform=linux/amd64 docker.io/condaforge/mambaforge:latest #force linux arch

# prerequisites
RUN ln -snf /usr/share/zoneinfo/$(curl https://ipapi.co/timezone) /etc/localtime

RUN apt-get update && \
    apt-get install -y --no-install-recommends build-essential && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# User creation
# RUN addgroup --gid 20 vscode
RUN adduser --disabled-password --gecos '' --uid 502 --gid 20 vscode
USER vscode

# install dependencies
COPY environment.yml .
RUN mamba env create -f environment.yml
