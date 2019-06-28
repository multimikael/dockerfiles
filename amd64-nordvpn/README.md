Run docker
```
docker run -ti --cap-add=NET_ADMIN --device /dev/net/tuns
```
The init.d script doesn't work properly with OpenRC. You need to start nordvpnd manually, before login.
```
nordvpnd &
nordvpn login
nordvpn connect
```