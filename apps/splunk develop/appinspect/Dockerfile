FROM centos:latest

RUN yum update -y
RUN dnf install -y http://repo.okay.com.mx/centos/8/x86_64/release/okay-release-1-5.el8.noarch.rpm
RUN dnf install -y epel-release
RUN dnf install -y 'dnf-command(config-manager)'
RUN dnf config-manager --add-repo /etc/yum.repos.d/CentOS-Linux-PowerTools.repo
RUN dnf config-manager --set-enabled powertools
RUN dnf upgrade -y
RUN yum install -y gcc make gcc-c++ wget git python39 python39-pip python39-devel python3-devel
RUN pip3 install pip --upgrade
RUN pip install splunk-appinspect
