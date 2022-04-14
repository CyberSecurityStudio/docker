#
# Declare the default image sources
#
FROM centos:latest

#
#  Convert from CentOS 8 to Centos Stream
#
RUN dnf --disablerepo '*' --enablerepo extras swap centos-linux-repos centos-stream-repos -y
RUN dnf distro-sync -y
RUN rm -f /etc/yum.repos.d/okay.repo

#
# Initial configurations of the docker image
#
RUN yum update -y
RUN dnf install -y http://repo.okay.com.mx/centos/8/x86_64/release/okay-release-1-5.el8.noarch.rpm
RUN dnf install -y epel-release

#
# Install the required software components from source repositories
#
RUN yum install -y gcc make cmake gcc-c++ wget git flex bison openssl-devel python3 python3-devel swig zlib-devel
RUN dnf --enablerepo=powertools install -y libpcap-devel
RUN pip3 install GitPython semantic-version

#
# Build and install the zeek software.
#
RUN cd /etc/yum.repos.d/ && wget https://download.opensuse.org/repositories/security:zeek/CentOS_8_Stream/security:zeek.repo
RUN yum install -y zeek

#
# Post configuration
#
RUN yum update -y
