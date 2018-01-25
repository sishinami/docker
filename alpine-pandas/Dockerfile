FROM alpine:3.7
MAINTAINER sysopjp

RUN apk add --no-cache python3-dev && \
    apk add --no-cache --virtual .build-deps g++ && \
    ln -s /usr/include/locale.h /usr/include/xlocale.h && \
    pip3 install numpy pandas && \
    apk del .build-deps

