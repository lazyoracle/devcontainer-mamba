FROM docker.io/condaforge/mambaforge:latest

# FROM --platform=linux/amd64 docker.io/condaforge/mambaforge:latest #force linux arch

# prerequisites
RUN ln -snf /usr/share/zoneinfo/$(curl https://ipapi.co/timezone) /etc/localtime

RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends -qq tzdata && \
    apt-get install -y --no-install-recommends fish wget bzip2 curl git gcc g++ build-essential cmake gnupg vim nano rsync htop tree screen && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN dpkg-reconfigure --frontend noninteractive tzdata

# install conda packages from file to base env
COPY environment.yml .
RUN mamba env update -n base -f environment.yml

# User creation
# RUN addgroup --gid 20 vscode
RUN adduser --disabled-password --gecos '' --uid 502 --gid 20 anurag
