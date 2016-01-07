# ssh

### Use SSH Keys Instead of Passwords

[Reference](https://www.digitalocean.com/community/tutorials/how-to-use-ssh-keys-with-digitalocean-droplets)

### 利用rsync断点续传

```zsh
# -P 部分传送和显示进度
# --rsh=ssh 使用ssh协议传送数据
rsync -P --rsh=ssh {{remote_path}} {{locale_path}}
```

或者方便一些设置一个alias:

```zsh
alias scpr="rsync -P --rsh=ssh"
```

只传送更新数据:

```zsh
# -a = -rlptgoD
# -u skip files that are newer on the receiver
scpr -au {{remote_path}} {{locale_path}}
```