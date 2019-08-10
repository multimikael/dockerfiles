# Usage
Pull from Docker hub and run docker
```
docker run -ti --cap-add=NET_ADMIN --device /dev/net/tun multimikael/alpine-nordvpn:amd64-latest
```
The init.d script doesn't work properly with OpenRC. You need to start nordvpnd manually, before login.
```
nordvpnd &
nordvpn login
nordvpn connect
```
# Issues
* IPv6 not disabled - TODO: Disable IPv6 through iptables
