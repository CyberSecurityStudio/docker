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

#
# Install the required software components from source repositories
#
RUN yum install -y gcc make gcc-c++ wget git flex bison libtool autoconf automake libtirpc-devel zlib-devel openssl-devel
RUN dnf install -y libmnl libmnl-devel libnfnetlink libnetfilter_queue
RUN dnf --enablerepo=powertools install -y libnfnetlink-devel libnetfilter_queue-devel nghttp2 libnghttp2-devel

#
# Compile the required sofware components from the source codes
#
RUN cd && wget http://luajit.org/download/LuaJIT-2.0.5.tar.gz && tar -zxvf LuaJIT-2.0.5.tar.gz && cd LuaJIT-2.0.5 && make && make install
RUN cd && wget http://www.tcpdump.org/release/libpcap-1.10.1.tar.gz && tar -zxvf libpcap-1.10.1.tar.gz && cd libpcap-1.10.1 && ./configure && make && make install
RUN cd && wget https://ixpeering.dl.sourceforge.net/project/pcre/pcre/8.45/pcre-8.45.tar.gz && tar -zxvf pcre-8.45.tar.gz && cd pcre-8.45 && ./configure && make && make install
RUN cd && git clone https://github.com/ofalk/libdnet && cd libdnet && libtoolize --copy --force && aclocal -I config && autoheader && autoconf && automake --add-missing && automake --foreign && ./configure && make && make install

#
# Build and install the DAQ modules with are required by Snort. The DAQ modules IPQ and netmap were not included.
#
RUN cd && wget https://snort.org/downloads/snort/daq-2.0.7.tar.gz && tar -zxvf daq-2.0.7.tar.gz && cd daq-2.0.7 && ./configure && make && make install

#
# Build and install the snort v2.9.
#
RUN cd && wget https://snort.org/downloads/snort/snort-2.9.18.1.tar.gz && tar -zxvf snort-2.9.18.1.tar.gz && cd snort-2.9.18.1 && ./configure && make && make install && ldconfig && ln -s /usr/local/bin/snort /usr/sbin/snort

#
# Clean up the local disk storage
#
RUN cd && rm -rf *.tar.gz && rm -rf LuaJIT-* && rm -rf lib* && rm -rf daq-* && rm -rf pcre-* && rm -rf snort-* 
