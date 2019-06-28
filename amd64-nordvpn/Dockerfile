FROM alpine:latest

ARG VER=3.1.0-6
RUN apk --no-cache add curl libarchive-tools net-tools libxslt iptables procps iproute2 musl
RUN curl -O https://repo.nordvpn.com/deb/nordvpn/debian/pool/main/nordvpn_${VER}_amd64.deb
#Maybe sha256sum the file
RUN bsdtar -O -xf nordvpn_${VER}_amd64.deb data.tar.xz | bsdtar -C / -xJf -
RUN rm nordvpn_${VER}_amd64.deb
#https://stackoverflow.com/a/35613430/9753282
RUN mkdir /lib64 && ln -s /lib/libc.musl-x86_64.so.1 /lib64/ld-linux-x86-64.so.2
#init.d script doesn't work properly
RUN nordvpnd > /dev/null &
