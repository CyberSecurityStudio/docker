FROM centos:latest

RUN yum update -y
RUN dnf install -y http://repo.okay.com.mx/centos/8/x86_64/release/okay-release-1-5.el8.noarch.rpm
RUN dnf install -y epel-release
RUN dnf install -y 'dnf-command(config-manager)'
RUN dnf config-manager --add-repo /etc/yum.repos.d/CentOS-Linux-PowerTools.repo
RUN dnf config-manager --set-enabled powertools
RUN dnf upgrade -y
RUN yum install -y gcc make gcc-c++ wget git automake autoconf libtool

# USER devuser
RUN yum install -y R
# RUN cd && wget https://download2.rstudio.org/rstudio-server-rhel-1.0.44-x86_64.rpm && yum install -y --nogpgcheck rstudio-server-rhel-1.0.44-x86_64.rpm

# EXPOSE 8787/tcp