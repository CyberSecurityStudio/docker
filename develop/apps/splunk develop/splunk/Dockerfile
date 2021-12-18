FROM centos:latest

RUN yum update -y
RUN dnf install -y http://repo.okay.com.mx/centos/8/x86_64/release/okay-release-1-5.el8.noarch.rpm
RUN dnf install -y epel-release
RUN dnf install -y 'dnf-command(config-manager)'
RUN dnf config-manager --add-repo /etc/yum.repos.d/CentOS-Linux-PowerTools.repo
RUN dnf config-manager --set-enabled powertools
RUN dnf upgrade -y

RUN yum install -y wget vim sudo
RUN cd && wget -O splunk-8.2.2.1-ae6821b7c64b-linux-2.6-x86_64.rpm https://d7wz6hmoaavd0.cloudfront.net/products/splunk/releases/8.2.2.1/linux/splunk-8.2.2.1-ae6821b7c64b-linux-2.6-x86_64.rpm && rpm -Uvh splunk-8.2.2.1-ae6821b7c64b-linux-2.6-x86_64.rpm && rm -f *
RUN echo -e  "\nOPTIMISTIC_ABOUT_FILE_LOCKING=1" >> /opt/splunk/etc/splunk-launch.conf

# Export the common network ports
EXPOSE 8000 8080 8089 8191 9997 9998 
EXPOSE 514 1514 2514 6514

ENV PATH="/opt/splunk/bin:${PATH}"
WORKDIR /opt/splunk