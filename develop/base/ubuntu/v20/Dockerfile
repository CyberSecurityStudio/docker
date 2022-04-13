FROM ubuntu:latest

RUN apt update -y && apt upgrade -y
ARG DEBIAN_FRONTEND=noninteractive
ENV TZ=Etc/UTC
RUN apt install -y tzdata

RUN apt install -y software-properties-common
RUN add-apt-repository ppa:remnux/stable
RUN apt-get update

RUN apt install -y git wget
