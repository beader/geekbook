# config


### Configurations

`~/.gitconfig`:

```
[user]
  name = name
  email = email
[core]
  autocrlf = input
[color]
  ui = true
[pull]
  rebase = true
[push]
  default = simple
[rerere]
  enabled = true
```


### Alias

```
git config --global alias.lg "log --oneline --decorate --all --graph"
```

### HTTPs Password Caching

```zsh
# on mac
git config --global credential.helper osxkeychain
# on linux
git config --global credential.helper cache
```
[Reference](
https://help.github.com/articles/caching-your-github-password-in-git/)