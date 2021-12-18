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
RUN yum install -y gcc make gcc-c++ wget git cmake autoconf automake libtool pkg-config flex bison compat-openssl10 openssl-devel openssl-libs jansson jansson-devel bind-lite-devel file-libs file-devel strace

#
# Build and install the yara binaries v4.1.1
#
RUN cd && git clone https://github.com/VirusTotal/yara && cd yara && ./bootstrap.sh && ./configure --enable-cuckoo --enable-magic --enable-dotnet --with-crypto && make && make install && ldconfig

#
# Clean up the local disk storage
#
RUN cd && rm -rf *
