# Dante over VPN

Designed to be used with [OpenVPN Client image](https://github.com/bjeanes/openvpn-client-docker), like so:

```
docker run -d --rm --cap-add=NET_ADMIN --device /dev/net/tun --name vpn ... bjeanes/openvpn-client -r ...
docker run -d --rm --net=container:vpn bjeanes/dante-vpn
```

Then, either use the container IP as the SOCKS proxy or add `-p 1080:1080` to
the VPN container run to use the host network as the proxy. `-p 1080:1080`
cannot be added to the dante container when it is using the VPN network.
