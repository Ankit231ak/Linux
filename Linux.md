
# Linux Notes

📘 These are my personal Linux notes – helpful commands, usage tips, and examples.  
✍️ Created by **Ankit Kumar**  
🗒️ For learning and quick reference.

---

## JSLinux – Virtual Linux on Browser  
🔗 [JSLinux (RISC-V)](https://bellard.org/jslinux/vm.html?cpu=riscv64&url=fedora33-riscv.cfg&mem=256)

---

## Basic Commands

- `clear` or `Ctrl + L` – Clear the terminal screen  
- `cd` – Move to the root directory (if used alone)  
- `pwd` – Print working directory  
- `whoami` – Show current user  
- `date` – Show current date and time  
  - `date +%D`, `date +%T`, etc.

---

## Listing Files – `ls`

| Command              | Description                                                              |
| -------------------- | ------------------------------------------------------------------------ |
| `ls -l`              | Long listing format (shows permissions, owner, size, date)               |
| `ls -a`              | Shows **all files**, including hidden files (`.` and `..`)               |
| `ls -la` or `ls -al` | Long listing **+** all files (common combo)                              |
| `ls -lh`             | Human-readable file sizes (e.g. KB, MB)                                  |
| `ls -R`              | Recursively list directories and subdirectories                          |
| `ls -lt`             | Sort by **modification time**, newest first                              |
| `ls -ltr`            | Sort by time, but in **reverse** (oldest first)                          |
| `ls -S`              | Sort by **file size**, largest first                                     |
| `ls -r`              | Reverse the order of the sort                                            |
| `ls -i`              | Show **inode** number of each file                                       |
| `ls -1` (one)        | Show **one file per line**                                               |
| `ls --color=auto`    | Colorized output based on file type (enabled by default in many distros) |

---

## File Reading & Editing

```bash
cat a.txt              # Read file
less a.txt             # View file with search and scroll (q to quit)
more a.txt             # View file, space to scroll
touch newFile.txt      # Create new file
rm newFile.txt         # Delete file
rm a b c temp temp2    # Remove multiple files
```

### Editing with Editors

```bash
vi text.txt
  i             # Insert mode
  Esc           # Exit insert mode
  :wq           # Save and quit
  :wq file      # Save and create if file doesn't exist

nano text.txt   # Simpler editor with features
```

---

## Folder Operations

```bash
mkdir fname      # Create folder
rmdir fname      # Delete empty folder
rm -rf fname     # Force delete folder
```

---

## Directory Navigation

```bash
cd a
cd a/axy/folder
cd ..
cd ../..
```

- **Absolute path**: Starts from root (`/`)
- **Relative path**: From current directory

---

## Copy and Move

```bash
cp file newFolder/newFile     # Copy to another folder
cp ../filename .              # Copy from previous to current
cp file newfile               # Copy and rename
mv file newFolder             # Move file
mv a b                        # Rename file or folder
```

---

## Head & Tail

```bash
head file.txt
head -n 5 file.txt

tail file.txt
tail -n 5 file.txt
```

---

## Pipes & Uniq & Sort

```bash
command1 | command2           # Pipe
uniq file                     # Show unique lines (case sensitive)
sort file.txt
sort -r file.txt              # Reverse
sort file | uniq              # Sort and remove duplicates
```

---

## File Splitting

```bash
split -l 3 file               # Split file into 3-line parts
```

---

## grep & egrep

```bash
grep "word" file
grep "word" file1 file2 file3
egrep "word|b|Bold" temp
grep -i -e "a" -e "b" temp.txt
```

---

## Wildcards

```bash
ls a*       # Starts with a
ls *a       # Ends with a
ls *a*      # Contains a
ls a*r      # Starts with a, ends with r
```

---

## File Batching & Shuffling

```bash
touch newFile{1..10}   # Create newFile1 to newFile10
shuf file              # Shuffle file lines
wc -l file             # Count file lines
```

---

## Compare Files

```bash
cmp fileA fileB        # Compare files
diff fileA fileB
diff -u fileA fileB
```

---

## Find Command

```bash
find . -name fileName
find .. -name fileName
find root/temp/bin/ -name fileName
```

---

## 🔐 sudo — Superuser Do

```bash
# Use sudo to gain elevated privileges
sudo -i                  # Become root temporarily
sudo apt install mlocate
sudo yum install mlocate
sudo updatedb
sudo updatedb --prunepaths="/mnt /lost+found /media"
locate fileName
```

---

## 📦 Package Managers

```bash
# APT
sudo apt update
sudo apt upgrade
sudo apt install nginx
sudo apt remove nginx
sudo apt search apache

# DNF/YUM
dnf list installed
dnf list installed | grep java
dnf list available
```

---

## 🕘 Command History

```bash
history
history | grep mkdir
```

---

## 📖 Help & Info

```bash
help
ls --help
man ls
which ls
which mkdir
```

---

## 🧮 Tools

```bash
bc              # Calculator
cal             # Calendar
cal 2025
uptime          # System uptime
```

---

## 📹 Terminal Recording

```bash
script          # Start recording
Ctrl+D          # Stop recording
```

---

## ⚡ Aliases

```bash
alias a="ls -ltr"
alias -p
unalias a
```

---

## 📦 File Compression

```bash
# Files
gzip -k file
gunzip file
gzip -d file

zip new.gz fileA fileB
unzip -l new.gz
unzip new.gz

# Folders
tar -czf temp.gz temp
tar -xzf temp.gz
```

---

## 🌐 Network & API

```bash
wget url
wget -O python https://www.python.org/ftp/python/3.13.5/python-3.13.5-amd64.exe

curl url
curl http://numbersapi.com/random
```

---

## 📦 Installed Packages

```bash
rpm -qa | grep appName
```

---

## 🧪 Environment & CSV

```bash
printenv                        # Show env variables
awk -F, '{print $2}' file.csv  # Print column
awk -F, '{print $NF}' file.csv
awk -F, '{print $1, $2}' file.csv
```

---

## 🧱 Change File Size

```bash
truncate -s 50M filename
```

---

## 🔄 Switch Users

```bash
su newUsername
```

---

## 👤 User Management

| Task                      | Command                                 |
| ------------------------- | --------------------------------------- |
| Create user (interactive) | `sudo adduser username`                 |
| Create user (quick)       | `sudo useradd -m -s /bin/bash username` |
| Set password              | `sudo passwd username`                  |
| Add user to sudo group    | `sudo usermod -aG sudo username`        |
| Delete user               | `sudo deluser username`                 |
| Delete user + home folder | `sudo deluser --remove-home username`   |



---

## 👥 User and Group Management

### Create a New Group:
```bash
groupadd group_name
```

### View All Groups:
```bash
cat /etc/group
```

### Check User ID:
```bash
id user_name
```

### Delete a User or Group:
```bash
sudo userdel user_name
sudo groupdel group_name
```

---

## 🔌 Networking & SSH

```bash
sudo apt install net-tools
sudo apt install openssh-server
sudo systemctl start ssh
sudo systemctl status ssh
ifconfig
ssh user@12.34.23.153                # Use IP address shown by ifconfig
# After running the `ssh` command, enter the user's password to connect.
```


---

## 👥 Find Users on Linux

```bash
who                                  # Show currently logged in users
cd /etc
less passwd                          # View user list from passwd file
/Administrator_Username              # Search for a specific username
# Press 'q' to quit
```

---

## 📤 Transfer Files from Your System to Linux

```bash
scp file user@hostname:/home/user/foldername
```



## 🔐 File Permissions & Ownership

### Permission Types:
- `r` : Read  
- `w` : Write  
- `x` : Execute  

### Permission Levels:
- `a` : All (user, group, others)  
- `u` : User  
- `g` : Group  
- `o` : Others  

### Modify File Permissions:
```bash
chmod a+rwx file      # Grant all permissions
chmod a-rwx file      # Remove all permissions
chown user file       # Change file owner
chgrp group file      # Change group owner
```

---

## 🧠 Memory & CPU Info

### Check Free RAM Space:
```bash
free
free -h     # Human-readable (MB/GB)
free -th    # Total summary
```

### Check CPU and Memory Usage:
```bash
top
```

### Check Folder Size:
```bash
du -h folder_name
```

### Check Disk Space:
```bash
df -h
df -h folder_name
```

---

## 🖥️ System Information

### Current Hostname:
```bash
hostname
```

### CPU/Core/Thread Info:
```bash
lscpu
```

### OS Info:
```bash
uname -a
```

---

## 🔍 Process Management

### Check If a Process Is Running:
```bash
ps -ef
ps -ef | grep process_name
```

### Get PID of a Process:
```bash
pgrep process_name
```

### Stop a Process by PID:
```bash
sudo kill -9 PID
```

### Stop a Process by Name:
```bash
pkill process_name
```

### Background Jobs:
```bash
sleep 10s
jobs
bg      # Move job to background
fg      # Bring background job to foreground
```

---

## 🔁 Reboot & Shutdown

### Reboot Linux Server:
```bash
sudo reboot
```

### Shutdown Linux Server:
```bash
sudo shutdown now
```

---

## ⏰ Schedule Tasks with `at`

The `at` command is used to schedule **one-time tasks** at a specific time.

### Install & Start `at` (if needed):
```bash
sudo apt install at
sudo systemctl start atd
sudo systemctl enable atd
```

### Schedule a Task:
```bash
at 2:30 PM
# Type your command, like:
echo "Backup done" >> backup.log
# Press Ctrl + D to confirm
```

### Time Formats:
- `now + 5 minutes`
- `10am tomorrow`
- `2pm next week`

### View Scheduled Tasks:
```bash
atq
```

### Remove a Scheduled Task:
```bash
atrm <job_number>
```

### Example:
```bash
echo "echo Hello >> hello.txt" | at now + 1 minute
```

---

## ➡️ Output Redirection

### Overwrite (`>`):
Redirects output and **overwrites** the file if it exists.

```bash
echo "Hello" > file.txt
```

### Append (`>>`):
Redirects output and **appends** to the file if it exists.

```bash
echo "World" >> file.txt
```

---

## 🙏 Thank You

Thanks for reading this Linux guide.  
Happy learning and exploring the terminal! 🧑‍💻🐧
