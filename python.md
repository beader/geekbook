# python

### pip

#### 从国内的mirror安装python package:
```zsh
# 注意后面要有/simple目录
pip install numpy -i https://pypi.mirrors.ustc.edu.cn/simple
```
国内的pipy镜像:

| url | 源 |
| -- | -- |
| https://pypi.douban.com/ | 豆瓣 |
| https://pypi.sdutlinux.org/  | 山东理工大学 |
| https://pypi.hustunique.com/ | 华中理工大学 |
| https://pypi.mirrors.ustc.edu.cn/ | 中国科学技术大学 |

配置成默认，可以修改 `~/.pip/pip.conf`:

```
[global]
index-url = https://pypi.mirrors.ustc.edu.cn/simple
```