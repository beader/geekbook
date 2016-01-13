# wget


### demo

下载页面上所有的pdf:

```zsh
wget --recursive --level=1 --no-directories --no-host-directories --accept pdf http://speech.ee.ntu.edu.tw/~tlkagk/courses_MLSD15_2.html
```

也可以简写成

```zsh
wget -r -l 1 -nd -nh -A pdf http://speech.ee.ntu.edu.tw/~tlkagk/courses_MLSD15_2.html
```