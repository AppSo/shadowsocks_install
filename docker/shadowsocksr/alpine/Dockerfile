# Dockerfile for ShadowsocksR based alpine
# Copyright (C) 2018 - 2019 AppSo
# Reference URL:
# https://github.com/AppSo/shadowsocksr

FROM python:3.6-alpine
LABEL maintainer="AppSo"

RUN runDeps="\
		tar \
		wget \
		libsodium-dev \
		openssl \
	"; \
	set -ex \
	&& apk add --no-cache --virtual .build-deps ${runDeps} \
	&& wget -O /tmp/shadowsocksr-3.1.2.tar.gz https://github.com/AppSo/shadowsocksr/archive/3.1.2.tar.gz \
	&& tar zxf /tmp/shadowsocksr-3.1.2.tar.gz -C /tmp \
	&& mv /tmp/shadowsocksr-3.1.2/shadowsocks /usr/local/ \
	&& rm -fr /tmp/shadowsocksr-3.1.2 \
	&& rm -f /tmp/shadowsocksr-3.1.2.tar.gz

COPY ./config_sample.json /etc/shadowsocksr/config.json
VOLUME /etc/shadowsocksr

USER nobody

CMD [ "/usr/local/shadowsocks/server.py", "-c", "/etc/shadowsocksr/config.json" ]
