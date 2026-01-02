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

## SQL

Common MariaDB/MySQL commands for database operations:

- Login: `mariadb -u username -p`
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

## Miscellaneous 

### Unzip to destination folder:

`unzip <zipfile> -d <destination>`

### Zipping a folder

`zip -r archive_name.zip folder_name/`

to exclude something

`zip -r zipname.zip folder_name -x "*.venv/*"`

### Extract `.tar.gz` File

`tar -xzf filename.tar.gz`

### Connect SSH

`sudo ssh -X -i <key> ubuntu@<ip>`

- where ubuntu is: `username`

### Detach from SSH

`Ctrl + d`
### Find process ID:

`ps aux`

### Batery percentage

`upower --dump`

### Get classname and some .desktop properties with cursor

`xprop`

### Searching on remote repositories (pacman)

`sudo pacman -Ss <search_term

### Start venv py3

`py -m venv .venv  "activate with source command in linux`

### Compile and link assembly (x86_64, Linux):

`nasm -f elf64 -g filename.asm -o objectfile.o && ld -m elf_x86_64 objectfile.o -o executable`

### Get images from docx
`unzip -l your_document.docx`
`mkdir docx_images`
`unzip -j your_document.docx "word/media/*" -d docx_images`


---

## Network Troubleshooting

- **Check DNS resolution:**

```bash
cat /etc/resolv.conf
nslookup google.com
```

- **Inspect interfaces and routing:**

```bash
ip addr show
ip route show
```

- **Restart NetworkManager (often fixes most issues):**

```bash
sudo systemctl restart NetworkManager
```

- **Reset networking stack (if still broken):**

```bash
sudo nmcli networking off
sudo nmcli networking on
```

- **Temporarily use Google DNS:**
```bash
echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf
```
---

## Audio & Microphone Fix

```bash
pulseaudio -k
pulseaudio -D
pavucontrol

```

## Greenclip (linux i3)

`nohup greenclip daemon &`
