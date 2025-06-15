## International Characters

### Unicode Codes

|Character|Description|Unicode|
|---|---|---|
|á|a with acute (Spanish)|`00e1`|
|é|e with acute (Spanish)|`00e9`|
|í|i with acute (Spanish)|`00ed`|
|ó|o with acute (Spanish)|`00f3`|
|ú|u with acute (Spanish)|`00fa`|
|ñ|n with tilde (Spanish)|`00f1`|
|Á|A with acute (Spanish)|`00c1`|
|É|E with acute (Spanish)|`00c9`|
|Í|I with acute (Spanish)|`00cd`|
|Ó|O with acute (Spanish)|`00d3`|
|Ú|U with acute (Spanish)|`00da`|
|Ñ|N with tilde (Spanish)|`00d1`|
|ü|u with diaeresis (Spanish/German)|`00fc`|
|Ü|U with diaeresis (Spanish/German)|`00dc`|
|¿|Inverted question mark (Spanish)|`00bf`|
|¡|Inverted exclamation mark (Spanish)|`00a1`|
|ä|a with umlaut (German)|`00e4`|
|ö|o with umlaut (German)|`00f6`|
|Ä|A with umlaut (German)|`00c4`|
|Ö|O with umlaut (German)|`00d6`|
|ß|Eszett (sharp S) (German)|`00df`|

---

## Neovim Tricks (some may work in vanilla vim too)

### Function Definition Search

Press `gd` in normal mode to find function definitions.

### English Dictionary

Enable with `setlocal spell spelllang=en`, check suggestions with `z=`, add words with `zg`.

keybind to enable dictionary: `mapleader + ss` in normal mode.

### Text Replacement

Use `:%s/foo/bar/g` to replace text globally (add `c` for confirmation).

### Buffer Navigation

Switch buffers with `:bn`, return to previous position using `Ctrl + o`.

### Code Formatting

Format with Prettier using `&lt;Leader&gt;p`, activate Copilot with `&lt;Leader&gt;t`.

### Accept copilot suggestion

`Ctrl + l`

---

## SQL

Common MariaDB/MySQL commands for database operations:

- Login: `sudo mariadb -u username -p`
- Service Management:
    - Start: `sudo systemctl start mariadb`
- Database Operations:
    - List databases: `SHOW DATABASES;`
    - Check current user: `SELECT CURRENT_USER();`
    - List tables: `SHOW TABLES;`
    - View table data: `SELECT * FROM table_name;`
- File Operations:
    - Run SQL file: `sudo mariadb -u username -p < file.sql`

---

## Miscellaneous Commands

### Get GitHub token:

`sudo grep 'GITHUB-DEVSETTINGS-TOKEN=' keys | sed 's/.*GITHUB-DEVSETTINGS-TOKEN=\\\\(.*\\\\)/\\\\1/' | wl-copy`

### Unzip to destination folder:

`unzip <zipfile> -d <destination>`

### Extract `.tar.gz` File

`tar -xzf filename.tar.gz`

### Find process ID:

`ps aux`

---

## Commitlint Common Types

According to [commitlint-config-conventional](https://github.com/conventional-changelog/commitlint):

- `build`
- `chore`
- `ci`
- `docs`
- `feat`
- `fix`
- `perf`
- `refactor`
- `revert`
- `style`
- `test`

---

## GitHub Initialization

```bash
git init
git add .
git commit -m "first commit"
git remote add origin <repo.git>
git branch -M main
git push -u origin main

```

---

## Tmux

### Reload configuration:

`tmux source-file ~/.tmux.conf`

### Vertical split:

`ctrl-command + %`

### Horizontal split:

`ctrl-command + "`

---

## Nmap

### First Touch Scan suggestion

`nmap -sC -sV -oA nmap/foldername <ip_address>`

### nmap flags in the command

- **-sC**: Runs default scripts, performing common security checks
- **-sV**: Probes open ports to determine service/version info
- **-oA**: Outputs scan results in three formats (normal, XML, and grepable) with the specified filename prefix

### suggested additional flags to enhance scans

- **-p-**: Scan all 65535 ports (more thorough but slower)
- **-T4**: Faster timing template (aggressive scan)
- **--open**: Only show open ports
- **-Pn**: Treat all hosts as online (skip host discovery)

---

## Assembly

### Compile and link assembly (x86_64, Linux):

`nasm -f elf64 -g filename.asm -o objectfile.o && ld -m elf_x86_64 objectfile.o -o executable`

---

## Network Troubleshooting

- Check DNS resolution:
    
    ```bash
    cat /etc/resolv.conf
    nslookup google.com
    
    ```
    
- Check network interface:
    
    ```bash
    ip link show
    ip addr show
    
    ```
    
- Check routing table:
    

`ip route show`

- Check NetworkManager logs:

`journalctl -u NetworkManager -n 50`

- Restart network interface:
    
    ```bash
    sudo ip link set wlan0 down
    sudo ip link set wlan0 up
    
    ```
    
- Clear DNS cache:
    

`sudo systemd-resolve --flush-caches`

- Reset network interface:
    
    ```bash
    sudo nmcli networking off
    sudo nmcli networking on
    
    ```
    
- Force reset NetworkManager:
    
    ```bash
    sudo systemctl stop NetworkManager
    sudo rm /var/lib/NetworkManager/NetworkManager.state
    sudo systemctl start NetworkManager
    
    ```
    
- Temporarily set Google DNS:
    

`echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf`

---

### SSH

### Connect

`sudo ssh -i <key> ubuntu@<ip>`

### Detach

`Ctrl + d`

---

---

## Audio & Microphone Fix

```bash
pulseaudio -k
pulseaudio -D
pavucontrol

```

---

## Stuck `sudo`

```bash
stty sane
# or
sudo pkill sudo

```

---

## HDMI Display Mirroring

```bash
xrandr --output HDMI-1 --same-as eDP-1 --auto

```

---

## Keyboard Issues

### Disable key repeat:

`xset -r`

### Re-enable key repeat:

`xset r`

---

## Neo-tree keybindings for navigation and file operations:

### Basic Navigation:

- `j` and `k`: Move up and down in the tree
- `t`: Open folder or open file in new tab
- `<C-t>`: Toggle Neo-tree window (we set this in the config)
- `<CR>` Open file/folder
- `.`: Set the root of the tree to current directory
- `<BS>` Go up one directory
- `h`: Toggle hidden files (.gitignore, .hidden, etc)

File Operations:

- `a`: Add a new file/directory (will prompt for name)
- `d`: Delete the file/directory under cursor
- `r`: Rename the file/directory under cursor
- `y`: Copy file name to system clipboard
- `Y`: Copy relative path to system clipboard
- `<C-y>`: Copy absolute path to system clipboard
- `c`: Copy file/directory to a destination
- `m`: Move file/directory to a destination

Working with Multiple Files:

- `<Space>`: Mark file (for bulk operations)
- `<C-Space>`: Clear marked files
- `s`: Open file in a split
- `S`: Open file in vertical split

Finding Files:

- `/`: Start a live filter of nodes in the tree
- `<C-x>`: Clear the live filter
- `<Esc>`: Clear live filter and cancel any operation
- `f`: Filter tree by pattern (more powerful than live filter)

Refresh and Git:

- `R`: Refresh the tree
- `?`: Open help menu with all keybindings
- `g?`: Show git status

Some Tips:

1. If you mark multiple files with `<Space>`, operations like delete will affect all marked files
2. The live filter (`/`) is great for quickly finding files in large projects

---

## Fonts

- 0xProto Nerd Font (supports many things)

### Installation

1. Unzip

`unzip ~/downloads/0xProto.zip -d ~/.local/share/fonts/`

1. Update Font Cache

`fc-cache -fv`

1. Verify

`fc-list | grep "0xProto"`

## Greenclip (linux i3)

`nohup greenclip daemon &`