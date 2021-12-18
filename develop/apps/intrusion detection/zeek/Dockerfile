FROM centos:latest

RUN yum update -y
RUN dnf install -y http://repo.okay.com.mx/centos/8/x86_64/release/okay-release-1-5.el8.noarch.rpm
RUN dnf install -y epel-release

RUN yum install -y gcc make cmake gcc-c++ wget git flex bison openssl-devel python3 python3-devel swig zlib-devel
RUN dnf --enablerepo=powertools install -y libpcap-devel
RUN pip3 install GitPython semantic-version

RUN cd /etc/yum.repos.d/ && wget https://download.opensuse.org/repositories/security:zeek/CentOS_8_Stream/security:zeek.repo
RUN yum install -y zeek

RUN yum update -y
