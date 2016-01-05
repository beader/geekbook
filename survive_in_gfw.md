# Survive in GFW

### 利用别人搭建的服务

| Name | Free | Description |
| -- | -- | -- |
| [Astrill](https://astrillaff.com/of2b824a) | No | Very Very Fast and easy to use |
| [lantern](https://github.com/getlantern/lantern) | Yes |  Lantern is a free desktop application that delivers fast, reliable and secure access to the open Internet for users in censored regions. |
| [鱼摆摆](https://ybb1024.com/) | No | Fast and cheap |
| [土豆VPN](https://www.tudouvpn.com/) | No | Pay as demand |
| [GREEN](http://gjsq.link/) | No | High CP Ratio|

### 自己搭建翻墙服务器

### 网络环境不好时的解决方案

### 如何在命令行下使用代理服务器

以鱼摆摆为例(astrill改变下端口号即可)，可以设置以下环境变量:

```zsh
export http_proxy=http://127.0.0.1:9743/
export https_proxy=http://127.0.0.1:9743/
```

设置后，`git`,`curl`,`wget`等命令会自动走代理。

对于ssh命令，可以通过设置`ProxyCommand`:

```zsh
ssh -o ProxyCommand='nc -x 127.0.0.1:9742 %h %p' root@主机IP
```

或者也可以编辑配置文件 `~/.ssh/config`

```zsh
ProxyCommand /usr/bin/nc -x 127.0.0.1:9742 %h %p
```
