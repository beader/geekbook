# Survive in GFW

### 利用别人搭建的服务

| Name | Free | Description |
| --- | --- | --- |
| [Astrill](https://astrillaff.com/of2b824a) | No | Very Very Fast and easy to use |
| [lantern](https://github.com/getlantern/lantern) | Yes | Lantern is a free desktop application that delivers fast, reliable and secure access to the open Internet for users in censored regions. |
| [鱼摆摆](https://ybb1024.com/) | No | Fast and cheap |
| [土豆VPN](https://www.tudouvpn.com/) | No | Pay as demand |
| [GREEN](http://gjsq.link/) | No | High CP Ratio |

### 自己搭建翻墙服务器

如果在国外拥有自己的VPS，可以搭建VPN，网上有很多参考资料。除了VPN外也可以尝试下shadowsocks，参考 [github/shadowsocks/shadowsocks](https://github.com/shadowsocks/shadowsocks/tree/2.8.2)

### 利用finalspeed为shadowsocks加速

FinalSpeed是高速双边加速软件,可加速所有基于tcp协议的网络服务,在高丢包和高延迟环境下,仍可达到90%的物理带宽利用率,即使高峰时段也能轻松跑满带宽。查看教程http://www.jianshu.com/p/970ceee01119

### 利用google app engine

[Google App Engine](https://cloud.google.com/appengine/)可以创建\(10个?\)免费的app，每个app每天有1G的免费流量，提供Go，Java，PHP，Python的运行环境，用来部署自己的网站或者是API服务。也有人利用它作为翻墙代理。比较有名的是goagent，但是该项目目前已经停止维护，有团队开发了个接力goagent的工具。参考[github/XX-net/XX-Net](https://github.com/XX-net/XX-Net/wiki)

### 网络环境不好时的解决方案

租一台最low的阿里云主机，带宽选20M以上，按流量付费，在上面搭一个openvpn。阿里云不论是国内线路还是国外线路速度都非常快，可以应对大部分网络环境不好的情况，比如长城宽带。

### 如何在命令行下使用代理服务器

以鱼摆摆为例\(astrill改变下端口号即可\)，可以设置以下环境变量:

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



