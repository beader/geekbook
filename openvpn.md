# openvpn

```sh
apt-get update
apt-get install openvpn easy-rsa
# example VPN server configuration
gunzip -c /usr/share/doc/openvpn/examples/sample-config-files/server.conf.gz > /etc/openvpn/server.conf
# open server.conf
vim /etc/openvpn/server.conf
```

字段说明

**固定用户IP**