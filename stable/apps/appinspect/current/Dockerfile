#
# Declare the default image sources
#
FROM alpine:latest
#
# Initial configurations of the docker image
#
RUN apk update && apk upgrade

#
# Install the required software components from source repositories
#
RUN apk add python3 python3-dev py3-pip gcc libstdc++ zlib zlib-dev libjpeg libmagic
RUN apk --update add libxml2-dev libxslt-dev libffi-dev gcc musl-dev libgcc openssl-dev curl
RUN apk add jpeg-dev zlib-dev freetype-dev lcms2-dev openjpeg-dev tiff-dev tk-dev tcl-dev
RUN pip3 install pip --upgrade

#
# Build and install the Splunk AppInspect application
#
RUN pip install splunk-appinspect
