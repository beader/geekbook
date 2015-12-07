# openvpn

#### 1. 安装

```zsh
apt-get update
apt-get install openvpn easy-rsa
```

#### 2. 生成服务器端证书，秘钥

- 复制秘钥生成工具到`/etc/openvpn`目录:
```zsh
cp -r /usr/share/easy-rsa/ /etc/openvpn
```

- 生成 Diffie-Hellman parameters:
```zsh
openssl dhparam -out /etc/openvpn/dh2048.pem 2048
```
- 设置`/etc/openvpn/easy-rsa/vars`:  
根据需要设置变量名，其中`KEY_NAME`是用来控制输出秘钥的文件名的，这里可以设置成:
```zsh
# /etc/openvpn/easy-rsa/vars
...
export KEY_NAME="server"
...
```
配置完`/etc/openvpn/easy-rsa/vars`后source一下
```zsh
cd /etc/openvpn/easy-rsa
source ./vars
./clean-all
```

- 生成ca:
```zsh
./build-ca
```
- 生成`certificate`和`key`:
```zsh
./build-key-server $KEY_NAME
```
中途询问输入密码，可以留空，直接按`ENTER`继续

这一步产生了服务器端需要的3个文件，把他们复制到`/etc/openvpn`目录下:
```
cp /etc/openvpn/easy-rsa/keys/{server.crt,server.key,ca.crt} /etc/openvpn
```

#### 3. 生成客户端证书，秘钥

以下会产生名为client1的证书以及秘钥文件，用相同的方法为多个客户端产生不同的证书及秘钥

```zsh
cd /etc/openvpn/easy-rsa
./build-key client1
```

#### 4. 网络配置


参考:

- [https://docs.ucloud.cn/software/vpn/OpenVPN4Ubuntu.html](OpenVPN for Ubuntu)
- [CentOS 6.3下OpenVPN实现双IDC互联](http://wangzan18.blog.51cto.com/8021085/1678272)
- [Linode VPS OpenVPN安装配置教程(基于Debian/Ubuntu)](http://www.vpser.net/build/linode-install-openvpn.html)
- [OpenVPN异地机房互连以及负载均衡高可用解决方案
](http://www.lxway.com/865859802.htm)
- [通过OpenWrt路由器和OpenVPN实现两地局域网互联](http://blog.ltns.info/linux/connect_two_home_networks_using_openvpn_and_openwrt/)