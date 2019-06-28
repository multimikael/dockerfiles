FROM alpine:latest


# Download and install NordVPN
ARG VER=3.1.0-6
#Maybe sha256sum the file
RUN apk --update --no-cache add curl libarchive-tools net-tools libxslt iptables procps iproute2 && \
    curl -O https://repo.nordvpn.com/deb/nordvpn/debian/pool/main/nordvpn_${VER}_amd64.deb && \
    bsdtar -O -xf nordvpn_${VER}_amd64.deb data.tar.xz | bsdtar -C / -xJf - && \
    rm nordvpn_${VER}_amd64.deb

# https://github.com/jeanblanchard/docker-alpine-glibc/blob/master/Dockerfile
# Download and install glibc
ENV GLIBC_VERSION 2.29-r0
RUN curl -Lo /etc/apk/keys/sgerrand.rsa.pub https://alpine-pkgs.sgerrand.com/sgerrand.rsa.pub && \
    curl -Lo glibc.apk "https://github.com/sgerrand/alpine-pkg-glibc/releases/download/${GLIBC_VERSION}/glibc-${GLIBC_VERSION}.apk" && \
    curl -Lo glibc-bin.apk "https://github.com/sgerrand/alpine-pkg-glibc/releases/download/${GLIBC_VERSION}/glibc-bin-${GLIBC_VERSION}.apk" && \
    apk add glibc-bin.apk glibc.apk && \
    /usr/glibc-compat/sbin/ldconfig /lib /usr/glibc-compat/lib && \
    echo 'hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4' >> /etc/nsswitch.conf && \
    rm -rf glibc.apk glibc-bin.apk /var/cache/apk/*
