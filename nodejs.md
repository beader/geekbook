# nodejs

### 1. install `npm` packages globally without sudo

1. Create a directory for globally packages
```zsh
mkdir "${HOME}/.npm-packages"
```
2. Indicate to `npm` where to store globally installed packages. In your `~/.npmrc` file add:
```zsh
# ~/.npmrc
prefix=${HOME}/.npm-packages
```
3.  Ensure `npm` will find installed binaries and man pages. Add the following to your `.bashrc` or `.zshrc`:
```zsh
NPM_PACKAGES="${HOME}/.npm-packages"
PATH="$NPM_PACKAGES/bin:$PATH"
# Unset manpath so we can inherit from /etc/manpath via the `manpath` command
unset MANPATH # delete if you already modified MANPATH elsewhere in your config
export MANPATH="$NPM_PACKAGES/share/man:$(manpath)"
```

reference is [here](https://github.com/sindresorhus/guides/blob/master/npm-global-without-sudo.md)

