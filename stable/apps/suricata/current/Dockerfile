#
# Declare the default image sources
#
FROM centos:latest

#
# Initial configurations of the docker image
#
RUN yum update -y
RUN dnf install -y http://repo.okay.com.mx/centos/8/x86_64/release/okay-release-1-5.el8.noarch.rpm
RUN dnf install -y epel-release
RUN yum update -y
RUN yum install -y gcc make gcc-c++ wget git python39

#
# Declare the default working directory
#
WORKDIR /root

#
# Install the required software components from source repositories
#
RUN yum install -y pcre pcre-devel jansson-devel libcap-ng-devel nspr-devel nss-devel lz4-devel rustc cargo zlib-devel
RUN dnf --enablerepo=powertools install -y libyaml-devel libpcap-devel file-devel
RUN pip3 install pyyaml

#
# Build and install the suricata software.
#
RUN cd && wget https://www.openinfosecfoundation.org/download/suricata-6.0.3.tar.gz
RUN tar -zxvf suricata-6.0.3.tar.gz 
RUN cd suricata-6.0.3 && ./configure && make && make install-full

#
# Post configuration
#
RUN cd && rm -rf suricata-6.0.3 && rm -f suricata-6.0.3.tar.gz 
RUN yum update -y
