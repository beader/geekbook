# vim

### ubuntu 下安装k-vim的一些列插件

先在vim当中运行`:version`

1. 查看是否是`7.4`以上的版本。如果出现`Small version without GUI.`等字样，还需要`vim-gui`与`vim-runtime`:
```zsh
# 参考:
# https://askubuntu.com/questions/284957/vi-getting-multiple-sorry-the-command-is-not-available-in-this-version-af
sudo apt-get install vim-gui-common
sudo apt-get install vim-runtime
```
2. 安装k-vim:
```zsh
# 参考:
# https://github.com/wklken/k-vim
sudo apt-get install ctags
sudo apt-get install build-essential cmake python-dev  #编译YCM自动补全插件依赖
sudo apt-get install silversearcher-ag
# python 相关
pip install pyflakes
pip install pylint
pip install pep8
# nodejs 相关
sudo apt-get install nodejs npm
npm install -g jslint
npm install jshint -g
# 安装 k-vim
git clone https://github.com/wklken/k-vim.git
cd k-vim/
sh -x install.sh
```

### mac 下安装 k-vim 系列插件

一直没有找到好的方法