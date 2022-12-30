# OTW-Bandit-Tutorial
## Intro
This is a quick guide made by your's truly to get you started in Over the Wire: Bandit, if you so choose. I recommend following along with the main website, and attempting all games before looking at solutions
*Main Website*: https://overthewire.org/wargames/bandit/

## Setup
 This assumes you have Virtual Box setup as your VM manager and a VM of Kali Linux. If you still need to set those up here's a tutorial:
*Virtual Box*: https://youtu.be/irGTD6jmYhc,
*Kali*: https://youtu.be/eLoxYXiQAPs 
## Kali
Once you've booted up Kali you'll be prompted to login, by default the username and password is `kali`. The after logging in hit `Ctrl+Alt+T` to open a terminal now you're ready to begin.

# Level 0
## Connection to Lvl 0
You'll the ssh command to connect, once you're done with a game use `exit` to close your ssh session and return to your machine's shell. 
```
ssh bandit0@bandit.labs.overthewire.org -p 2220
passwd: bandit0
```
You'll use the same command to enter further levels
```
ssh bandit{Level Number}@bandit.labs.overthewire.org -p(ort) 2220
```
## Lvl 0
Once you've connected to Lvl 0 use the `ls` command to list all the files in your current directory. You should now see a `readme` file. Use `cat` to view the passwd for level 1. Double click to highlight it and use `Ctrl+Shift+C` to copy it to your clipboard, then use  `exit` to exit Lvl 0.

# Level 1
## Connection to Lvl 1
The process for connecting to Lvl 1 is almost identical as Lvl 0. Except you'll need to change the Lvl number in the ssh command and you'll be prompted for a password. To start hit the `Up Arrow` to scroll through your previously used commands until you get to the `ssh` command you used to connect to Lvl 0. Simply change `0` to `1` and when prompted use `Ctrl+Shift+V` to paste the password you got from Lvl 0. Don't worry that you can see what you just pasted, linux hides passwords when you're entering them.
