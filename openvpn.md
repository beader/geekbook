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

参考:

- [CentOS 6.3下OpenVPN实现双IDC互联](http://wangzan18.blog.51cto.com/8021085/1678272)
- [Linode VPS OpenVPN安装配置教程(基于Debian/Ubuntu)](http://www.vpser.net/build/linode-install-openvpn.html)
- [OpenVPN异地机房互连以及负载均衡高可用解决方案
](http://www.lxway.com/865859802.htm)
- [通过OpenWrt路由器和OpenVPN实现两地局域网互联](http://blog.ltns.info/linux/connect_two_home_networks_using_openvpn_and_openwrt/)