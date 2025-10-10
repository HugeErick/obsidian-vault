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

## Filezilla to share files is the best option

## ZEROSSL WORKED WITH REVERSE NGINX!!!

## Neovim Tricks (some may work in vanilla vim too)

### Life-changing Basics

```
:q!         " Quit without saving (force quit)
:saveas ~/new/path.txt  " Save current file with new name/path
:r filename " Insert contents of another file here
:r !ls      " Insert output of shell command (ls, date, etc)

```

### Navigation

```
gd          " Go to function definition under cursor
gf          " Go to file under cursor (great for code)
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

### Search Techniques

```
/pattern\\\\c   " Search without case sensitivity
/\\\\cpattern   " Alternative method for case-insensitive search

```

### Pro Tips & Hidden Gems

```
:!python %   " Run current Python file
:!node %     " Run current JavaScript file
:!gcc % && ./a.out  " Compile and run C program
:help tutor  " Run vimtutor inside Vim!
:help usr_02.txt " User manual chapter 2 (basic editing)
:helpgrep pattern " Search all help files

```

### Language Tools

```
" English Dictionary
setlocal spell spelllang=en
z=          " Check spelling suggestions
zg          " Add word to dictionary
<leader>ss  " Keybind to enable dictionary (normal mode)

```

### AI Assistance

```
<Leader>p   " Format with Prettier
<Leader>t   " Activate Copilot
Ctrl + l    " Accept copilot suggestion

```

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

### Unzip to destination folder:

`unzip <zipfile> -d <destination>`

### Zipping a folder

`zip -r archive_name.zip folder_name/`

to exclude something

`zip -r zipname.zip folder_name -x "*.venv/*"`

### Extract `.tar.gz` File

`tar -xzf filename.tar.gz`

### Find process ID:

`ps aux`

### Batery percentage

`upower —dump`

### Get classname and some .desktop properties with cursor

`xprop`

### Searching on remote repositories (pacman)

`sudo pacman -Ss <search_term

### Start venv py3

`py -m venv .venv  "activate with source command in linux`

### Compile and link assembly (x86_64, Linux):

`nasm -f elf64 -g filename.asm -o objectfile.o && ld -m elf_x86_64 objectfile.o -o executable`

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

`nmap -sC -sV -vv -O -oA ~/poly/nmap/foldername/ <ip_address>`

### nmap flags in the command

- **-sC**: Runs default scripts, performing common security checks
- **-sV**: Probes open ports to determine service/version info
- *-*vv: extra verbose
- **-O** OS fingerprinting

Nmap sends a special set of TCP, UDP and ICMP probes whose subtle variations in window size, TTL, DF bit, TOS, sequence numbers, etc. create a unique “fingerprint.”

- **-oA**: Outputs scan results in three formats (normal, XML, and grepable) with the specified filename prefix

### suggested additional flags to enhance scans

- **-p-**: Scan all 65535 ports (more thorough but slower)
- **-T4**: Faster timing template (aggressive scan)
- **--open**: Only show open ports
- **-Pn**: Treat all hosts as online (skip host discovery)

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

`sudo ssh -X -i <key> ubuntu@<ip>`

where ubuntu is: `username`

### Detach

`Ctrl + d`

---

## Audio & Microphone Fix

```bash
pulseaudio -k
pulseaudio -D
pavucontrol

```

---
## HDMI Display Mirroring

```bash
xrandr --output HDMI-1 --same-as eDP-1 --auto

```

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

## Update windsurf with source tarball

### 1. Remove the old installation

```bash
sudo rm -rf /opt/windsurf
```

### 2. Extract the tarball

```bash
cd ~/downloads
tar -xvzf Windsurf-linux.tar.gz
```

This will give you a fresh `Windsurf/` or `Windsurf-linux-x64-1.12.3/` folder.

### 3. Move it to `/opt`

```bash
sudo mv Windsurf /opt/windsurf
```

(or if the folder is named differently, adjust accordingly)

### 4. Recreate the symlink

Remove the old one just in case:

```bash
sudo rm -f /usr/local/bin/windsurf
```

Then make the new link (check if the binary is lowercase or uppercase):

```bash
sudo ln -s /opt/windsurf/windsurf /usr/local/bin/windsurf
```

## Discord

### Secc Acc

mail: `dravenmid62@gmail.com`

user: `massiveAnalizer`

psw: `z`

## Firefox custom config (about:config)
### External  and internal link opening firefox

Change the preference for `browser.link.open_newwindow.override.external` to `3` to open external links in a new tab in the last active window instead opening new instance, for internal links verify that the value of `browser.link.open_newwindow` is also set to 3.

### Adjusting Firefox DPI settings

modify `layout.css.devPixelsPerPx` (default is `-1.0` which uses system DPI)

### Disable private translations 
`browser.translations.enable` set it to false