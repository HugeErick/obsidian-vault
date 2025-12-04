### Essential Shortcuts (Prefix: `Ctrl+b`)

- `Ctrl+b c` - Create new window
- `Ctrl+b n` - Next window
- `Ctrl+b p` - Previous window
- `Ctrl+b 0-9` - Switch to window number 0-9
- `Ctrl+b %` - Split pane vertically
- `Ctrl+b "` - Split pane horizontally
- `Ctrl+b arrow` - Switch between panes
- `Ctrl+b x` - Close current pane
- `Ctrl+b d` - Detach from session

### list sessions
`tmux ls`

### attach session
`tmux a -t sessionname`

### kill session
`tmux kill-session -t sessionname`

## fzf

### with the help of having the fzf defaults bash loaded in .bashrc

```bash
[ -f ~/.fzf.bash ] && source ~/.fzf.bash
```

### Ctrl + r 
`Gives the history of commands`
### Ctrl + t
`Gives file search`

### Custom cdf command
`does change dir where the file selected with fzf is`
