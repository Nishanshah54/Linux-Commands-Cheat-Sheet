# Linux Commands Cheat Sheet

A comprehensive reference for commonly used Linux commands, organized by category.

---

## Table of Contents

- [File Operations](#file-operations)
- [Directory Operations](#directory-operations)
- [File Viewing](#file-viewing)
- [Search Commands](#search-commands)
- [Permissions & Ownership](#permissions--ownership)
- [Process Management](#process-management)
- [System Information](#system-information)
- [Networking](#networking)
- [Text Processing](#text-processing)
- [Compression & Archiving](#compression--archiving)
- [Package Management](#package-management)
- [User Management](#user-management)
- [Shortcuts & Tips](#shortcuts--tips)
- [Quick Reference Card](#quick-reference-card)
- [Learning Resources](#learning-resources)

---

## File Operations

### `cat` — Concatenate and Display Files
Purpose: View file contents or combine files

```bash
# View single file
cat file.txt

# View multiple files
cat file1.txt file2.txt

# Create new file
cat > newfile.txt

# Append to file
cat >> existing.txt
```

### `cp` — Copy Files/Directories

```bash
# Copy file
cp source.txt destination.txt

# Copy directory recursively
cp -r source_dir/ destination_dir/

# Preserve file attributes
cp -p file.txt backup/
```

### `mv` — Move/Rename Files

```bash
# Rename file
mv oldname.txt newname.txt

# Move file to directory
mv file.txt /path/to/directory/

# Move multiple files
mv *.txt /path/to/directory/
```

### `rm` — Remove Files/Directories

```bash
# Remove file
rm file.txt

# Remove directory recursively
rm -r directory/

# Force remove without confirmation
rm -rf directory/

# Remove empty directory
rmdir directory/
```

### `touch` — Create Empty File

```bash
# Create new file
touch newfile.txt

# Update file timestamp
touch existing.txt
```

### `ln` — Create Links

```bash
# Create hard link
ln original.txt link.txt

# Create symbolic link
ln -s /path/to/original linkname
```

---

## Directory Operations

### `mkdir` — Make Directory

```bash
# Create single directory
mkdir newdir

# Create nested directories
mkdir -p parent/child/grandchild

# Create multiple directories
mkdir dir1 dir2 dir3
```

### `cd` — Change Directory

```bash
cd ~        # Home directory
cd          # Home directory
cd ..       # Parent directory
cd -        # Previous directory
cd /        # Root directory
```

### `pwd` — Print Working Directory

```bash
pwd
```

### `ls` — List Directory Contents

```bash
ls      # Basic
ls -l   # Long format
ls -la  # Include hidden files
ls -lh  # Human-readable sizes
ls -lt  # Sort by modification time
ls -R   # Recursive
```

### `rmdir` — Remove Empty Directory

```bash
rmdir emptydir
rmdir -p parent/child/
```

---

## File Viewing

### `head`

```bash
head file.txt
head -n 20 file.txt
head -c 50 file.txt
```

### `tail`

```bash
tail file.txt
tail -n 20 file.txt
tail -f logfile.log
```

### `less` / `more`

```bash
less file.txt
less -N file.txt
more file.txt
```

### Editors: `nano`, `vim`, `vi`

```bash
nano file.txt
vim file.txt
vi file.txt
```

---

## Search Commands

### `grep`

```bash
grep "pattern" file.txt
grep -i "pattern" file.txt
grep -r "pattern" directory/
grep -n "pattern" file.txt
grep -v "pattern" file.txt
grep -c "pattern" file.txt
grep -w "word" file.txt
grep -e "p1" -e "p2" file.txt
```

### `find`

```bash
find . -name "*.txt"
find . -type d -name "dirname"
find . -type f -mtime -7
find . -type f -size +10M
find . -name "*.tmp" -exec rm {} \;
```

### `locate`, `which`, `whereis`

```bash
locate filename.txt
sudo updatedb
which ls
whereis ls
```

---

## Permissions & Ownership

### Permission Basics

- Format: `-rwxr-xr--`
- Octal values: r=4, w=2, x=1

Examples:
- `754` → `rwxr-xr--`
- `644` → `rw-r--r--`

### `chmod`

```bash
chmod u+x file.txt
chmod g-w file.txt
chmod o=r file.txt
chmod a+x file.txt
chmod -R 755 directory/
chmod 644 file.txt
```

### `chown` / `chgrp`

```bash
sudo chown user file.txt
sudo chown user:group file.txt
sudo chown -R user:group directory/
chgrp newgroup file.txt
chgrp -R newgroup directory/
```

### `umask`

```bash
umask
umask 022
```

---

## Process Management

### `ps`

```bash
ps aux
ps -u $USER
ps auxf
ps aux --sort=-%cpu
ps aux --sort=-%mem
```

### `top` / `htop`

```bash
top
htop
```

### `kill`, `pkill`, `killall`

```bash
kill PID
kill -9 PID
killall processname
pkill processname
```

### Job Control

```bash
jobs
fg %1
bg %1
command &
```

### Priority & Persistence

```bash
nice -n 10 command
renice -n 5 -p PID
nohup command &
```

---

## System Information

```bash
uname -a
df -h
du -sh directory/
free -h
uptime
who
w
date
cal
```

---

## Networking

```bash
ping google.com
ip addr show
ip route show
ss -tulpn
curl https://example.com
wget https://example.com/file.zip
ssh user@hostname
scp file.txt user@hostname:/path/
rsync -av source/ destination/
```

---

## Text Processing

```bash
sort file.txt
uniq -c file.txt
wc -l file.txt
cut -d',' -f1 file.csv
awk '{print $1}' file.txt
sed 's/old/new/g' file.txt
tr 'a-z' 'A-Z' < file.txt
diff -u file1.txt file2.txt
```

---

## Compression & Archiving

```bash
tar -czvf archive.tar.gz files/
tar -xzvf archive.tar.gz
gzip file.txt
gunzip file.txt.gz
zip archive.zip file1.txt file2.txt
unzip archive.zip
```

---

## Package Management

### APT (Debian/Ubuntu)

```bash
sudo apt update
sudo apt upgrade
sudo apt install package
sudo apt remove package
```

### YUM / DNF

```bash
sudo yum install package
sudo dnf update
```

### Pacman (Arch)

```bash
sudo pacman -Syu
```

---

## User Management

```bash
whoami
id
passwd
sudo adduser username
sudo userdel -r username
groups
sudo usermod -aG group username
```

---

## Shortcuts & Tips

### Keyboard Shortcuts

- `Ctrl+C` – Terminate command
- `Ctrl+Z` – Suspend process
- `Ctrl+D` – Logout / EOF
- `Ctrl+L` – Clear screen
- `Ctrl+R` – Search history
- `Tab` – Auto-complete

### Useful Aliases

```bash
alias ll='ls -la'
alias rm='rm -i'
alias cp='cp -i'
alias mv='mv -i'
```

---

## Quick Reference Card

### Common Commands

```bash
ls cd pwd cp mv rm mkdir cat grep find chmod chown ps kill sudo
```

### Common Options

- `-r`, `-R` – Recursive
- `-f` – Force
- `-i` – Interactive
- `-v` – Verbose
- `-h` – Human readable

---

## Learning Resources

- `man <command>` / `<command> --help`
- Linux Journey
- Linux Command Library
- *The Linux Command Line* — William Shotts
- *How Linux Works* — Brian Ward

> **Reminder:** With great power comes great responsibility. Be extremely cautious with commands like `rm -rf`, `chmod`, and `chown`, especially when used with `sudo`.

