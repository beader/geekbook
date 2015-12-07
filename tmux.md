# tmux

- [[TMUX] 基本操作心得_tmux command](http://imdori.blogspot.tw/2013/10/tmux-tmux-command.html)
- [進化版 screen - tmux](http://josephj.com/entry.php?id=373)
- [tmux: Productive Mouse-Free Development](https://aquaregia.gitbooks.io/tmux-productive-mouse-free-development_zh/content/)

`.tmux.conf` 参考配置:

```
set -sg escape-time 1
set -g base-index 1
setw -g pane-base-index 1
set -g prefix C-a
unbind C-b
bind C-a send-prefix
bind | split-window -h
bind - split-window -v
bind h select-pane -L
bind j select-pane -D
bind k select-pane -U
bind l select-pane -R
setw -g mode-mouse on
set -g mouse-select-pane on
set -g mouse-resize-pane on
set -g mouse-select-window on
```