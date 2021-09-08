FROM centos:latest

RUN yum update -y
RUN dnf install -y http://repo.okay.com.mx/centos/8/x86_64/release/okay-release-1-5.el8.noarch.rpm
RUN dnf install -y epel-release
RUN yum update -y
RUN yum install -y gcc make gcc-c++ wget git
