# Docker Hub Mirror

使用Docker时，`docker pull [image]` 默认是从 [docker hub](https://hub.docker.com/) 拉取，如果机器在国内，速度会很慢。这时候可以通过替换 docker hub mirror 国内镜像。国内较有名的docker hub mirror有 [DaoCloud](http://daocloud.io/) 和 [阿里云](http://aliyun.com)。

## DaoCloud 镜像

注册好 DaoCloud 后进入 dashboard。点击 `加速器`，即可看到属于你的镜像地址，以及修改镜像地址的方法。


## 阿里云 镜像

注册阿里云，进入控制台，进入[Docker镜像仓库](https://cr.console.aliyun.com)，点击加速器，可以看到镜像地址以及配置方法。