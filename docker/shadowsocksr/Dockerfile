# Dockerfile for ShadowsocksR
# Copyright (C) 2018 - 2019 AppSo
# Reference URL:
# https://github.com/AppSo/shadowsocksr

FROM debian:stretch
LABEL maintainer="AppSo"

RUN set -ex \
	&& apt-get update \
	&& apt-get install -y wget python libsodium-dev openssl \
	&& rm -rf /var/lib/apt/lists/* \
	&& wget -O /tmp/shadowsocksr-3.1.2.tar.gz https://github.com/AppSo/shadowsocksr/archive/3.1.2.tar.gz \
	&& tar zxf /tmp/shadowsocksr-3.1.2.tar.gz -C /tmp \
	&& mv /tmp/shadowsocksr-3.1.2/shadowsocks /usr/local/ \
	&& rm -fr /tmp/shadowsocksr-3.1.2 \
	&& rm -f /tmp/shadowsocksr-3.1.2.tar.gz

COPY ./config_sample.json /etc/shadowsocksr/config.json
VOLUME /etc/shadowsocksr

USER nobody

CMD [ "/usr/local/shadowsocks/server.py", "-c", "/etc/shadowsocksr/config.json" ]
