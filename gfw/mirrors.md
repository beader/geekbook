# Mirrors

### ubuntu - apt source-list

```zsh
$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
$ sudo vi /etc/apt/sources.list
```

```zsh
# /etc/apt/sources.list
deb http://mirrors.aliyun.com/ubuntu/ trusty main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ trusty-security main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ trusty-updates main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ trusty-proposed main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty-security main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty-updates main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty-proposed main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty-backports main restricted universe multiverse
```

### nodejs - npm

modify `~/.npmrc`

```zsh
# ~/.npmrc
registry = https://registry.npm.taobao.org
```

### python - pip

See [this](python/pip.html)

### docker

See [this](http://www.imike.me/2016/04/20/Docker%E4%B8%8B%E4%BD%BF%E7%94%A8%E9%95%9C%E5%83%8F%E5%8A%A0%E9%80%9F/)