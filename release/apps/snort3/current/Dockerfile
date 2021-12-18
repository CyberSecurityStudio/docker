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
RUN yum remove -y libuv1 
RUN yum install -y gcc make gcc-c++ wget git libuv

#
# Install the required software components from source repositories
#
RUN yum install -y cmake flex bison libtool autoconf automake libtirpc-devel zlib-devel openssl-devel strace
RUN dnf install -y libpcap-devel pcre-devel libdnet-devel hwloc-devel openssl-devel zlib-devel luajit-devel pkgconfig libnfnetlink-devel libnetfilter_queue-devel libmnl-devel libunwind-devel xz-devel libuuid-devel hyperscan hyperscan-devel gperftools-devel
RUN dnf install -y libsafec libsafec-devel && ln -s /usr/lib64/pkgconfig/safec-3.3.pc /usr/lib64/pkgconfig/libsafec.pc

#
# Compile the required sofware components from the source codes
#
RUN cd && git clone https://github.com/snort3/libdaq.git && cd libdaq && ./bootstrap && ./configure && make && make install && ldconfig
RUN cd && git clone https://github.com/google/flatbuffers && cd flatbuffers && cmake . && make -j$(nproc) &&  make -j$(nproc) install && ldconfig

#
# Build and install the snort v3.1.12
#
RUN cd && git clone https://github.com/snort3/snort3.git && cd snort3 && export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig:$PKG_CONFIG_PATH && export PKG_CONFIG_PATH=/usr/local/lib64/pkgconfig:$PKG_CONFIG_PATH && ./configure_cmake.sh --prefix=/usr/local/snort --enable-tcmalloc && cd build && make -j$(nproc) && make -j$(nproc) install && ldconfig
RUN ln -s /usr/local/snort/bin/snort /usr/sbin/snort && ln -s /usr/local/lib/libdaq.so.3.0.0 /lib64/libdaq.so.3

#
# Build and install the exrta snort components
#
RUN cd && git clone https://github.com/snort3/snort3_extra && cd snort3_extra && export PKG_CONFIG_PATH=/usr/local/snort/lib64/pkgconfig:$PKG_CONFIG_PATH && ./configure_cmake.sh --prefix=/usr/local/snort/extra && cd build && make -j$(nproc) && make -j$(nproc) install 

#
# Clean up the local disk storage
#
RUN cd && rm -rf snort* lib* flat*
