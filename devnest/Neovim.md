### Basics

```
:saveas ~/new/path.txt  " Save current file with new name/path
:r filename " Insert contents of another file here
:r !ls      " Insert output of shell command (ls, date, etc)
gd          " Go to function definition under cursor
gf          " Go to file under cursor
Ctrl-o      " Jump back to previous location
Ctrl-i      " Jump forward
:ju         " Show jump list (history of where you've been)

```

### Advanced Editing

```
Ctrl-a      " Increment number under cursor
Ctrl-x      " Decrement number under cursor
gv          " Reselect last visual selection
:set paste  " Turn on paste mode (prevents formatting mess)
:set nopaste " Turn it off
* (in visual mode) " searches selected pattern 

```

### File Management

```
:Explore    " Open file explorer (or :Sex for split)
:ls         " List all open buffers
:b 2        " Switch to buffer number 2
:bd         " Close current buffer (keep window open)
:bn         " Switch to next buffer

```

### Text Operations

```
:%s/foo/bar/g " Replace text globally (add 'c' for confirmation)

```

### Search  & Jump Techniques

```
/pattern\c   " Search without case sensitivity
/\cpattern   " Alternative method for case-insensitive search
  " Set a Mark:
Press `m` followed by any letter (e.g., `ma`).
    
  " Teleport back:
Press `'` (apostrophe) followed by that letter (e.g., `'a`).

```

### Pro Tips & Hidden Gems

```
:!python %   " Run current Python file
:!node %     " Run current JavaScript file
:!gcc % && ./a.out  " Compile and run C program
:help tutor  " Run vimtutor inside Vim!
:help usr_02.txt " User manual chapter 2 (basic editing)
:lua vim.diagnostic.goto_next() " Goes to the next error (lsp)

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
```

### AI Assistance

```
<Leader>t   " Activate Copilot
Ctrl + l    " Accept copilot suggestion

```

---
## Neo-tree

`.` makes select node root