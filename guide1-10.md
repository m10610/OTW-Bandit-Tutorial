# OTW-Bandit-Levels 1-10 Field Notes
May 26 2023 Ver.
## 0
```
ssh bandit0@bandit.labs.overthewire.org -p 2220
passwd: bandit0
```
1. `ls` view files
2. `cat {file}` view file contents
    - use `-n` to display line numbers ex: `cat -n {file}`
3. `exit` to leave bandit0

---
## 1
Use `./{file}` to reference a filename including special characters

---
## 2
Use quotes or double quotes wrapped around a filename to reference a filename with spaces
```
cat 'spaced file name'
cat "spaced file name"
```

---
## 3
1. Used `cd` to change directories
    - `cd new_directory`
2. Use the `-a` option with the `ls` cmd to view all files including hidden files (prefixed with a .)
    - `ls -a`

---
## 4
Couple different approaches varying in complexity **EDIT**: I did not read the website, and did not realize the intended way to solve the level, refer to solution D (Although sol. C does work)
- A. Use lvl 1 Notes
    1. use `cat ./{file}` to search manually 
- B. Use the `*` (wildcard operator), Matches zero or more characters.    
    - For example, \*.txt matches all files ending with ".txt", and file\* matches all files starting with "file"
    1. `cat ./*` cat all files within the active directory, this works and you'll be able to generally tell where the password but since the text is quite jumbled it's hard to know which files contains it or where it starts and ends 
- C. Use regular expression patterns, now these are tricky and usually pretty annoying but when you get them right they're incredibly useful
    - regex patterns as they're better known by, filter ASCII strings (text)
    - This command searches all the contents of each file in the current directory and displays only those with a line containing upper/lowercase letters and digits 
        - `grep -P '^[a-zA-Z0-9]+$' ./*`
    - The `grep` command, it's incredibly useful for filtering so I recommend looking into it if you haven't already
    - The `-P` option is used to enable Perl-compatible regular expressions (PCRE) which is a modified version of regex that allows for more functionality  
    - `'^[a-zA-Z0-9]+$'` the PCRE pattern searches for an entire line that consists solely of one or more case-insensitive letters or digits from start to end
        -  useful website to create/test regex patterns [here](https://regexr.com/) (or use chat-gpt to create them like a sane person)
    - `./*` sets search scope to all files in current directory
- D. `file ./*` displays the file type of each file 

---
## 5
- `find -size 1033c -type f`
    - `find` searches for files
    - `-size 1033c` filters to exactly 1033 bytes
    - `-type f` filters to normal files

---
## 6
- `find / -type f -user bandit7 -group bandit6 -size 33c`
    - `find` searches for files
    - `-type f` filters to normal files
    - `-user bandit7` filters to owned by user bandit7
    - `-group bandit6` filters to owned by group bandit6
    - `-size 33c` filters to exactly 33 bytes
- Furthermore you can add `2>/dev/null` to the end of the command to filter out error messages (throws the errors into a trashcan)
    - `find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null`
    - `2>` signifies that your redirecting stderr (standard error)(basically any result that is classified as an error) to a different location
    - `/dev/null` is basically a trashcan, anything put it gets deleted

---
## 7
- Either works
    - `cat data.txt | grep millionth` 
    - `grep millionth ./data.txt` 
    - filters out lines not containing `millionth`

---
## 8
- `cat data.txt | sort | uniq -u`
    - `cat file |` get contents of file and pipes to sort
    - `sort |` sort list alphabetically for `uniq` to work properly then pipes to `uniq`
    - `uniq -u` filters to unique lines

---
## 9
- `strings data.txt | grep =`
    - `strings` filters out non-human readable lines
    - `grep =` filters to just lines with `=`

---
## 10
- `cat data.txt | base64 -d`
    - `base64 -d` decodes base64 data into plain text