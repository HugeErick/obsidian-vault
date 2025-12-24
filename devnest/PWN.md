## First blood:

```bash
objdump
checksec
```

# GDB (Pwngdb) Cheatsheet

## Execution Commands

- `r` (run): Start program execution from the beginning
- `c` (continue): Continue execution until next breakpoint or program termination
- `ni` (next instruction): Step over function calls, executing entire function as one step
- `si` (step instruction): Step into function calls, entering the function
- `fin` (finish): Complete execution of current function and stop at return
- `bt` (backtrace): Display stack trace/call stack
- `frame` or `f`: Navigate between stack frames

## Breakpoint Management

- `b` or `break function_name`: Set breakpoint at function start
- `b *0x12345678`: Set breakpoint at specific memory address
- `info b`: List all breakpoints
- `delete breakpoint #`: Remove specific breakpoint
- `disable/enable breakpoint #`: Temporarily disable/enable breakpoint

## Memory Examination

### Basic Examine Command: `x`

Syntax: `x/[quantity][format][size] address`

### Quantity Modifiers

- `20`: Number of units to display
- Default is 1 if omitted

### Format Specifiers

- `x`: Hexadecimal
- `d`: Decimal
- `u`: Unsigned decimal
- `c`: Character
- `s`: String
- `i`: Instruction

### Size Specifiers

- `b`: Byte (1 byte)
- `h`: Halfword (2 bytes)
- `w`: Word (4 bytes)
- `g`: Giant word (8 bytes)

### Examples

- `x/20gx $rsi`:
    - Examine 20 units
    - `g`: Giant word (8 bytes)
    - `x`: Hexadecimal format
    - `$rsi`: Register to examine
- `x/s $rax`: Examine string at address in RAX
- `x/10i $rip`: Disassemble 10 instructions from current instruction pointer

## Register Inspection

- `info registers`: Display all register contents
- `p $rax`: Print value of RAX register
- `p/x $rax`: Print RAX in hexadecimal
- `p/t $rax`: Print RAX in binary

## Function Address Retrieval

- `p function_name`: Prints function's memory address
- `info address function_name`: Get detailed address information
- `disas function_name`: Disassemble function

## Memory/Stack Manipulation

- `set $rax=0x1234`: Set register value
- `watch *0x12345678`: Stop when memory address changes
- `print *(int *)0x12345678`: Dereference memory address

## Process and Symbol Information

- `info proc mappings`: Display memory mappings
- `info sharedlibrary`: List loaded shared libraries
- `info functions`: List all function symbols
- `info variables`: List global/static variables

## Useful Pwn-specific Commands

- `pattern create 100`: Generate unique pattern for buffer overflow
- `pattern offset $rsp`: Find offset in pattern
- `telescope`: Recursively dereference memory (Pwngdb extension)

## Configuration

- `.gdbinit`: Configuration file in home directory
- Recommended Pwngdb/GEF/Pwndbg plugins for enhanced debugging

## Launching

- `gdb ./binary`: Start GDB with binary
- `gdb -q ./binary`: Quiet mode (suppress intro message)
- `gdb -ex "command" ./binary`: Execute command on startup

## Tips

- Use `layout asm` for assembly view
- `set disassembly-flavor intel`: Switch to Intel syntax
- `record` and `reverse-stepi` for reverse debugging

## Common Keyboard Shortcuts

- `Ctrl+X+A`: Toggle between text/assembly/source views
- `Ctrl+L`: Clear screen
- `Ctrl+P/N`: Previous/Next command history
## Nmap

### First Touch Scan suggestion

`nmap -sC -sV -vv -O -oA ~/poly/nmap/foldername/ <ip_address>`

### nmap flags in the command

- **-sC**: Runs default scripts, performing common security checks
- **-sV**: Probes open ports to determine service/version info
- **-vv**: extra verbose
- **-O** OS fingerprinting

Nmap sends a special set of TCP, UDP and ICMP probes whose subtle variations in window size, TTL, DF bit, TOS, sequence numbers, etc. create a unique “fingerprint.”

- **-oA**: Outputs scan results in three formats (normal, XML, and grepable) with the specified filename prefix

### suggested additional flags to enhance scans

- **-p-**: Scan all 65535 ports (more thorough but slower)
- **-T4**: Faster timing template (aggressive scan)
- **--open**: Only show open ports
- **-Pn**: Treat all hosts as online (skip host discovery)
- __--script=banner__ To see whats likely behind the port 
- __-sU__ Scans the UDP ports 
---

`nmap -p1-65535 -sS -T4 143.110.227.127`
This command performs a **stealthy, full port scan** on the target IP address `143.110.227.127` at a **fast speed**. Its goal is to find every single open TCP port on the machine, from the first to the last possible port, without completing the full TCP connection handshake.

## FTP
File transfer protocol; if the target machine has an ftp port open anywhere (defaults ports can be changed)
`ftp <ip>`
then we can try accessing in anonymous mode

## NC
Netcat is an universal tool for interacting with network services

## DIG
The dig command

## After gaining access to a console/terminal

### Ask the OS to list open ports
`ss -tunlp`
