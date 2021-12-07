FROM alpine:latest

RUN sudo apk update && sudo apk upgrade
RUN apk add python3 python3-dev py3-pip gcc libstdc++ zlib zlib-dev libjpeg libmagic
RUN apk --update add libxml2-dev libxslt-dev libffi-dev gcc musl-dev libgcc openssl-dev curl
RUN apk add jpeg-dev zlib-dev freetype-dev lcms2-dev openjpeg-dev tiff-dev tk-dev tcl-dev
RUN pip3 install pip --upgrade
RUN pip install splunk-appinspect