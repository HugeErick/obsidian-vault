<C-a> = ctrl + a

### navigation & jumping

```
gd  " go to function definition under cursor
gf  " go to file under cursor
<C-o>  " jump back to previous location
<C-i>  " jump forward
:ju  " show jump list
/pattern\c  " search without case sensitivity
ma  " set mark a at current position
'a  " jump to mark a
:delmarks!  " delete all marks
:ls  " list all open buffers
:b 2  " switch to buffer number 2
:bn  " switch to next buffer
<C-d> " jumps down half screen
<C-u> " jumps up half screen
{ and } "jump to the next/previous empty line (great for jumping over whole functions).
```

### editing & manipulation

```
<C-a>  " increment number under cursor
<C-x>  " decrement number under cursor
gv  " reselect last visual selection
(visual) U  " make text uppercase
(visual) u  " make text lowercase
:%s/foo/bar/g  " replace text globally
:r filename  " insert contents of another file
:r !ls  " insert output of shell command
:saveas path.txt  " save current file with new name
:set paste  " turn on paste mode
:set nopaste  " turn off paste mode
* " (in visual mode) search selected pattern

```

### workflow & system

```
:vsplit  " split window vertically
:split  " split window horizontally
:Explore  " open file explorer
:bd  " close current buffer
:!python %  " run current file with python
:!node %  " run current file with node
:!gcc % && ./a.out  " compile and run c program
:PeekOpen  " open markdown preview in browser
:lua vim.diagnostic.goto_next()  " jump to next lsp error
:help tutor  " run vimtutor
:help usr_02.txt  " open user manual chapter 2
:map <leader>a  "shows all bindings for that key in all modes
:verbose map <leader>a  "verbose mode of showing all bindings for that key in all modes
:nmap  " list all normal mode maps
:vmap  " list all visual mode maps
:imap  " list all insert mode maps
<leader>vs " selects venv for lsp (py)

```

### Extra

```
" English Dictionary
setlocal spell spelllang=en "dictionary in english
z=          " Check spelling suggestions
zg          " Add word to dictionary
<leader>ss  " Keybind to enable dictionary (normal mode)
<leader>ll  " Compile latex
<leader>th  " toggle theme
<leader>f  " search files starting 1 folder up (fzf)
<leader>F  " search files in current directory (fzf)
<leader>fb  " search through open buffers (fzf)
<leader>fl  " search lines in current file (fzf)
:echo line('.') " shows total lines in buffer

```

## Neo-tree

```
`.` makes select node root
`<leader>d` toggles between neo-tree and main buffer
`<leader>e` toggles activating neo-tree (files sidebar)
`backspace` makes the previous folder the new node root

```

