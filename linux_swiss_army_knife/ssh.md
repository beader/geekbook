# ssh

### scp 断点续传

[Reference](http://blog.csdn.net/hepeng597/article/details/8960885)

```zsh
# -P 部分传送和显示进度
# --rsh=ssh 使用ssh协议传送数据
rsync -P --rsh=ssh remote_location local_location
```

或者方便一些设置一个alias:

```zsh
alias scpr="rsync -P --rsh=ssh"
```