ARG BUILD_FROM
FROM $BUILD_FROM

ARG BUILD_ARCH

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y -q --install-recommends --no-install-suggests nano tzdata procps curl iputils-ping telnet

RUN curl -s https://packagecloud.io/install/repositories/crowdsec/crowdsec/script.deb.sh | bash

RUN apt-get update
RUN apt-get install -y -q --install-recommends --no-install-suggests crowdsec-cloudflare-bouncer
RUN rm -rf /var/lib/apt/lists/*

# Copy root filesystem
COPY rootfs /