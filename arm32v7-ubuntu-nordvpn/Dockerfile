FROM arm32v7/ubuntu:latest

# Download and install NordVPN
ARG VER=3.3.0-4

RUN apt-get update && apt-get install -y curl bsdtar libxslt1.1 iproute2 iptables net-tools procps && \
    curl -O https://repo.nordvpn.com/deb/nordvpn/debian/pool/main/nordvpn_${VER}_armhf.deb && \
    bsdtar -O -xf nordvpn_${VER}_armhf.deb data.tar.xz | bsdtar -C / -xJf - && \
    rm nordvpn_${VER}_armhf.deb

CMD [ "systemctl start nordvpnd" ]