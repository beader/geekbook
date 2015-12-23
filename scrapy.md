# scrapy

错误信息:

```zsh
[boto] ERROR: Caught exception reading instance data
```
add the following to your settings.py file:

```zsh
# settings.py
DOWNLOAD_HANDLERS : {
    's3': None,
}
```