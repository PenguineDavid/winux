# winux

**winux** is a Linux-like shell and coreutils environment for Windows, written in Python.

It provides a Unix-style command line experience on native Windows without relying on WSL, BusyBox, or Cygwin.  
Commands are implemented as real Windows executables, enabling correct piping, redirection, job control, and signal handling.

---

## Features

### Shell
- Linux-style prompt (`user@host:cwd$`)
- Command pipelines (`|`)
- Input/output redirection:
  - `>`, `>>`, `<`
  - `2>`, `2>&1`
  - `&>`
- Background jobs (`&`)
- Job control:
  - `jobs`
  - `fg`
  - `bg`
- Ctrl+C / Ctrl+Break forwarding to foreground processes
- Works on Windows and Unix-like systems

### Built-in Commands
- `cd` (supports `cd -`)
- `ls` / `dir` (`-a`, `-l`)
- `mkdir` (`-p`, `-v`)
- `touch` (`-c`)
- `rm` (`-r`, `-f`, `-i`, `-v`)
- `cp` (files only)
- `eval`
- `help`
- `version`

### External Core Utilities (compiled as `.exe`)
Implemented as standalone executables for correct stream behavior:

- `cat`
- `echo`
- `pwd`
- `find`
- `grep`
- `head`
- `tail`
- `yes`
- `less`
- `more`

These behave like real Unix tools and fully support piping and redirection on Windows.

---

## SSH Support

- `ssh user@host`
  - Interactive remote shell using Paramiko
- `scp user@host:/path/to/file .`
  - Remote → local copy via SFTP

---

## Why Executables Instead of Built-ins?

Windows handles pipes and redirection at the process level.  
By compiling core utilities into real executables:

- `stdout` / `stderr` behave correctly
- `cmd > file` works as expected
- `cmd | other_cmd` streams properly
- Buffering issues are avoided

This mirrors how Unix shells and coreutils actually work.

---

## Installation

### Requirements
- Python 3.9+
- Windows 10+ (primary target)
- needs a path environmental variable
### Running the Shell

```CMD
winux


