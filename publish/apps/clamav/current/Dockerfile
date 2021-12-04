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
RUN dnf install -y 'dnf-command(config-manager)'
RUN dnf config-manager --add-repo /etc/yum.repos.d/CentOS-Linux-PowerTools.repo
RUN dnf config-manager --set-enabled powertools
RUN dnf upgrade -y

#
# Install the required software components from source repositories
#
RUN yum install -y gcc make gcc-c++ wget git python3 python3-pip valgrind bzip2-devel check-devel json-c-devel libcurl-devel libxml2-devel ncurses-devel openssl-devel pcre2-devel sendmail-devel zlib-devel
RUN python3 -m pip install cmake

#
# Build and install the clamav 0.105.0
#
RUN cd && git clone https://github.com/Cisco-Talos/clamav && cd clamav && mkdir build && cd build && cmake .. && cmake --build . && ctest && cmake --build . --target install

#
# Post configuration and clean up
#
RUN cd && rm -rf *
