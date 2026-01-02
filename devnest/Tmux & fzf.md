## Tmux

- Prefix = ctrl + x

`prefix + c`  create new window
`prefix + n`  next window
`prefix + p`  previous window
`prefix + 0-9`  switch to window number 0-9
`prefix + %`  split pane vertically
`prefix + "`  split pane horizontally
`prefix + arrow`  switch between panes
`prefix + x`  close current pane
`prefix + d`  detach from session

`tmux ls` list sessions 
`tmux a -t sessionname` attach session
`tmux kill-session -t sessionname` kill session

### Custom

`prefix + r` tmux source-file the .tmux.conf

(works thanks to key tables)
`prefix + gi` opens github repo that may have the current path


## fzf

### With the help of having the fzf defaults bash loaded in .bashrc

```bash
[ -f ~/.fzf.bash ] && source ~/.fzf.bash
```

`ctrl + r` gives the history of commands
`ctrl + t` gives file search
`cdf` does change dir where the file selected with fzf is``

