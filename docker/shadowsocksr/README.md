## ShadowsocksR Docker Image

[shadowsocksr][1] is a lightweight secured socks5 proxy for embedded devices and low end boxes.
It is a port of [shadowsocks][2] created by @clowwindy maintained by @breakwa11 and @Akkariiin.

Docker images are built for quick deployment in various computing cloud providers.
For more information on docker and containerization technologies, refer to [official document][3].

## Prepare the host

If you need to install docker by yourself, follow the [official installation guide][4].

## Pull the image

```bash
$ docker pull appso/shadowsocksr
```

or pull image based **alpine**

```bash
$ docker pull appso/shadowsocksr:alpine
```


This pulls the latest release of shadowsocksr.

It can be found at [Docker Hub][5].

## Start a container

You **must create a configuration file**  `/etc/shadowsocksr/config.json` in host at first, and sample:

```
{
    "server":"0.0.0.0",
    "server_ipv6":"::",
    "server_port":443,
    "local_address":"127.0.0.1",
    "local_port":1080,
    "password":"password",
    "timeout":120,
    "method":"none",
    "protocol":"auth_chain_b",
    "protocol_param":"",
    "obfs":"tls1.2_ticket_auth",
    "obfs_param":"",
    "redirect":"",
    "dns_ipv6":false,
    "fast_open":false,
    "workers":1
}
```

This container with sample configuration `/etc/shadowsocksr/config.json`

There is an example to start a container that listens on `443` (both TCP and UDP):

```bash
$ docker run -d -p 443:443 -p 443:443/udp --name ssr -v /etc/shadowsocksr:/etc/shadowsocksr appso/shadowsocksr
```

There is an example to start a container based **alpine** that listens on `443` (both TCP and UDP):

```bash
$ docker run -d -p 443:443 -p 443:443/udp --name ssr -v /etc/shadowsocksr:/etc/shadowsocksr appso/shadowsocksr:alpine
```

**Note**: The port number must be same as configuration.

[1]: https://github.com/AppSo/shadowsocksr
[2]: https://shadowsocks.org/en/index.html
[3]: https://docs.docker.com/
[4]: https://docs.docker.com/install/
[5]: https://hub.docker.com/r/appso/shadowsocksr/
