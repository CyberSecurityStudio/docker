FROM centos:latest

RUN yum update -y
RUN dnf install -y http://repo.okay.com.mx/centos/8/x86_64/release/okay-release-1-5.el8.noarch.rpm
RUN dnf install -y epel-release
RUN dnf install -y 'dnf-command(config-manager)'
RUN dnf config-manager --add-repo /etc/yum.repos.d/CentOS-Linux-PowerTools.repo
RUN dnf config-manager --set-enabled powertools
RUN dnf upgrade -y

# RUN wget -O splunk-8.2.2.1-ae6821b7c64b-linux-2.6-x86_64.rpm 'https://d7wz6hmoaavd0.cloudfront.net/products/splunk/releases/8.2.2.1/linux/splunk-8.2.2.1-ae6821b7c64b-linux-2.6-x86_64.rpm'
# RUN wget -O splunk-8.2.2.1-ae6821b7c64b-Linux-x86_64.tgz 'https://d7wz6hmoaavd0.cloudfront.net/products/splunk/releases/8.2.2.1/linux/splunk-8.2.2.1-ae6821b7c64b-Linux-x86_64.tgz'
# RUN wget -O splunk-8.2.2.1-ae6821b7c64b-linux-2.6-amd64.deb 'https://d7wz6hmoaavd0.cloudfront.net/products/splunk/releases/8.2.2.1/linux/splunk-8.2.2.1-ae6821b7c64b-linux-2.6-amd64.deb'
#RUN wget -O splunkforwarder-8.2.2.1-ae6821b7c64b-Linux-x86_64.tgz 'https://d7wz6hmoaavd0.cloudfront.net/products/universalforwarder/releases/8.2.2.1/linux/splunkforwarder-8.2.2.1-ae6821b7c64b-Linux-x86_64.tgz'
#RUN wget -O splunkforwarder-8.2.2.1-ae6821b7c64b-linux-2.6-amd64.deb 'https://d7wz6hmoaavd0.cloudfront.net/products/universalforwarder/releases/8.2.2.1/linux/splunkforwarder-8.2.2.1-ae6821b7c64b-linux-2.6-amd64.deb'
# RUN wget -O splunkforwarder-8.2.2.1-ae6821b7c64b-linux-2.6-x86_64.rpm 'https://d7wz6hmoaavd0.cloudfront.net/products/universalforwarder/releases/8.2.2.1/linux/splunkforwarder-8.2.2.1-ae6821b7c64b-linux-2.6-x86_64.rpm'

RUN yum install wget vim -y
RUN cd && wget -O splunkforwarder-8.2.2.1-ae6821b7c64b-linux-2.6-x86_64.rpm 'https://d7wz6hmoaavd0.cloudfront.net/products/universalforwarder/releases/8.2.2.1/linux/splunkforwarder-8.2.2.1-ae6821b7c64b-linux-2.6-x86_64.rpm' && rpm -Uvh splunkforwarder-8.2.2.1-ae6821b7c64b-linux-2.6-x86_64.rpm && rm -f *

USER root
WORKDIR /opt/splunkforwder
