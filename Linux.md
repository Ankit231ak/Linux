# Linux Notes

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

- `cat a.txt` – Read file
- `less a.txt` – Scroll (`/n`, `?n`), use `Shift+G`, `Shift+P`, `q` to quit
- `more a.txt` – Read file, use `Space` to move next page
- `touch newFile.txt` – Create new file
- `rm newFile.txt` – Delete file
- `rm a b c temp temp2` – Remove multiple files

### File Editing

- `vi text.txt`
  - `i` – Insert mode
  - `Esc` – Exit insert mode
  - `:wq` – Save and quit
  - `:wq file` – Save and create if file doesn't exist
- `nano text.txt` – Easier editor with additional features

---

## Folder Operations

- `mkdir fname` – Create folder
- `rmdir fname` – Delete empty folder
- `rm -rf fname` – Delete folder (forcefully)

---

## Directory Navigation

- `cd a`
- `cd a/axy/folder`
- `cd ..` – Move up one level
- `cd ../..` – Move up two levels

**Absolute path**: Starts from root  
**Relative path**: Starts from current directory

---

## Copy and Move

- `cp file newFolder/newFile` – Copy to other folder
- `cp ../filename .` – Copy from previous folder to current (`.` = current)
- `cp file newfile` – Copy and rename
- `cp file ../newfile` – Copy to parent folder

- `mv file newFolder` – Move file to folder
- `mv a b` – Rename file or folder

---

## Viewing File Lines

- `head file.txt` – Top 10 lines
- `head -n 5 file.txt` – Top 5 lines

- `tail file.txt` – Last 10 lines
- `tail -n 5 file.txt` – Last 5 lines

---

## Piping & Filtering

- `|` – Pipe to combine commands
- `uniq file` – Filter unique lines (case-sensitive)
- `sort file.txt`
- `sort -r file.txt` – Reverse sort
- `sort file | uniq` – Sort and remove duplicates

---

## File Splitting

- `split -l 3 file` – Split file into parts, 3 lines each

---

## Grep – Searching

- `grep "word" file` – Search word in file
- `grep "word" file1 file2 file3` – Search in multiple files
- `egrep "word|b|Bold" temp` – OR condition with multiple words
- `grep -i -e "a" -e "b" temp.txt` – Ignore case, multiple patterns

---

## Wildcards

- `ls a*` – Files starting with 'a'
- `ls *a` – Files ending with 'a'
- `ls *a*` – Files containing 'a'
- `ls a*r` – Files starting with 'a' and ending with 'r'

---

## Batch File Creation

- `touch newFile{1..10}` – Create newFile1 to newFile10

---

## Miscellaneous

- `shuf file` – Shuffle lines in file
- `wc -l file` – Count lines in file

---

## File Comparison

- `cmp fileA fileB` – Compare files, only shows first difference
- `diff fileA fileB` – Show differences
- `diff -u fileA fileB` – Unified diff

---

## File Search

- `find . -name fileName`
- `find .. -name fileName`
- `find root/temp/bin/ -name fileName`
