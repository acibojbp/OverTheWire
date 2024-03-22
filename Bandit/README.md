# Bandit Solutions and Writeups

https://overthewire.org/wargames/bandit/

Welcome to the Bandit directory! Here, you'll find my solutions and insights for each level of the OverTheWire Bandit wargame.

Get started by exploring the very first challenge of '[Bandit Level 0](#bandit-level-0)' and progress through the final stages. Explore how I've improved my **Linux command-line** skills and learned about **privilege escalation** techniques through these challenges.

## Disclaimer
_The solutions shared in this repository are intended solely for educational purposes. They are provided to aid in learning and understanding cybersecurity concepts related to Linux command-line usage and privilege escalation. Any use of these solutions for unauthorized or unethical purposes is strongly discouraged._
## Contents

| Bandit Level 0 → 10       | Bandit Level 10 → 20       | Bandit Level 20 → 30       | Bandit Level 30 → 33       |
|---------------------------|----------------------------|----------------------------|----------------------------|
| [Bandit Level 0 → Level 1](#bandit-level-0--level-1)     | [Bandit Level 10 → Level 11](#bandit-level-10--level-11) | [Bandit Level 20 → Level 21](#bandit-level-20--level-21) | [Bandit Level 30 → Level 31](#bandit-level-30--level-31) |
| [Bandit Level 1 → Level 2](#bandit-level-1--level-2)  | [Bandit Level 11 → Level 12](#bandit-level-11--level-12) | [Bandit Level 21 → Level 22](#bandit-level-21--level-22) | [Bandit Level 31 → Level 32](#bandit-level-31--level-32) |
| [Bandit Level 2 → Level 3](#bandit-level-2--level-3)  | [Bandit Level 12 → Level 13](#bandit-level-12--level-13) | [Bandit Level 22 → Level 23](#bandit-level-22--level-23) | [Bandit Level 32 → Level 33](#bandit-level-32--level-33) |
| [Bandit Level 3 → Level 4](#bandit-level-3--level-4)  | [Bandit Level 13 → Level 14](#bandit-level-13--level-14) | [Bandit Level 23 → Level 24](#bandit-level-23--level-24) |                            |
| [Bandit Level 4 → Level 5](#bandit-level-4--level-5)  | [Bandit Level 14 → Level 15](#bandit-level-14--level-15) | [Bandit Level 24 → Level 25](#bandit-level-24--level-25) |                            |
| [Bandit Level 5 → Level 6](#bandit-level-5--level-6)  | [Bandit Level 15 → Level 16](#bandit-level-15--level-16) | [Bandit Level 25 → Level 26](#bandit-level-25--level-26) |                            |
| [Bandit Level 6 → Level 7](#bandit-level-6--level-7)  | [Bandit Level 16 → Level 17](#bandit-level-16--level-17) | [Bandit Level 26 → Level 27](#bandit-level-26--level-27) |                            |
| [Bandit Level 7 → Level 8](#bandit-level-7--level-8)  | [Bandit Level 17 → Level 18](#bandit-level-17--level-18) | [Bandit Level 27 → Level 28](#bandit-level-27--level-28) |                            |
| [Bandit Level 8 → Level 9](#bandit-level-8--level-9)  | [Bandit Level 18 → Level 19](#bandit-level-18--level-19) | [Bandit Level 28 → Level 29](#bandit-level-28--level-29) |                            |
| [Bandit Level 9 → Level 10](#bandit-level-9--level-10) | [Bandit Level 19 → Level 20](#bandit-level-19--level-20) | [Bandit Level 29 → Level 30](#bandit-level-29--level-30) |                            |

# Bandit Level 0

## Level Goal

The goal of this level is for you to log into the game using SSH. The host to which you need to connect is **bandit.labs.overthewire.org**, on port 2220. The username is **bandit0** and the password is **bandit0**. Once logged in, go to the [Level 1](https://overthewire.org/wargames/bandit/bandit1.html) page to find out how to beat Level 1.
## Commands you may need to solve this level

[ssh](https://man7.org/linux/man-pages/man1/ssh.1.html)
## Helpful Reading Material

- [Secure Shell (SSH) on Wikipedia](https://en.wikipedia.org/wiki/Secure_Shell)
- [How to use SSH on wikiHow](https://www.wikihow.com/Use-SSH)

## Solution

```
SSH Information  
Host: bandit.labs.overthewire.org  
Port: 2220
```

- Before starting, create a folder and go inside that folder. This is for keeping things organized.
```
cd /home/kali/overthewire/bandit      
```

- This is where we will store the passwords and other relevant resources.
- Install `sshpass` for easy ssh logins.
```
sudo apt update
sudo apt install sshpass
```
  
- This code will connect to `ssh` using the password saved in `bandit(x)`, where x is the level.
```
sshpass -p `cat bandit(x)` ssh bandit(x)@bandit.labs.overthewire.org -p 2220
```

- Save looted passwords in their respective files `bandit(x)` inside `/home/kali/overthewire/bandit`

# Bandit Level 0 → Level 1

## Level Goal

The password for the next level is stored in a file called **readme** located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

## Commands you may need to solve this level

[ls](https://man7.org/linux/man-pages/man1/ls.1.html) , [cd](https://man7.org/linux/man-pages/man1/cd.1p.html) , [cat](https://man7.org/linux/man-pages/man1/cat.1.html) , [file](https://man7.org/linux/man-pages/man1/file.1.html) , [du](https://man7.org/linux/man-pages/man1/du.1.html) , [find](https://man7.org/linux/man-pages/man1/find.1.html)

## Solution

```
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

Password for this level is bandit0

The password is inside the file **readme** in the **home** directory.
We can view this file using the command `ls`
```
bandit0@bandit:~$ ls
readme
```

To read the contents of a file, use the command `cat <filename>`
```
bandit0@bandit:~$ cat readme
NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL
```

And we get the password to the next level.
Logout of `ssh` using `Ctrl + D`.
Save the file to bandit1 using `nano`

#  Bandit Level 1 → Level 2

## Level Goal

The password for the next level is stored in a file called **-** located in the home directory

## Commands you may need to solve this level

[ls](https://man7.org/linux/man-pages/man1/ls.1.html) , [cd](https://man7.org/linux/man-pages/man1/cd.1p.html) , [cat](https://man7.org/linux/man-pages/man1/cat.1.html) , [file](https://man7.org/linux/man-pages/man1/file.1.html) , [du](https://man7.org/linux/man-pages/man1/du.1.html) , [find](https://man7.org/linux/man-pages/man1/find.1.html)

## Helpful Reading Material

- [Google Search for “dashed filename”](https://www.google.com/search?q=dashed+filename)
- [Advanced Bash-scripting Guide - Chapter 3 - Special Characters](http://tldp.org/LDP/abs/html/special-chars.html)

## Solution

Connect to this level using the newly saved password in bandit1 by running the command :
```
sshpass -p `cat bandit1` ssh bandit1@bandit.labs.overthewire.org -p 2220
```

In this level, the password is inside the file named `-`
We cannot simply use `cat -`

Running this command does not return anything and if we type something it just returns what we typed. We can stop this using `Ctrl + C`.

To properly print out the contents of the file we must first specify the path with `./`
```
bandit1@bandit:~$ cat ./-
rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi
```

# Bandit Level 2 → Level 3

## Level Goal

The password for the next level is stored in a file called **spaces in this filename** located in the home directory
## Commands you may need to solve this level

[ls](https://man7.org/linux/man-pages/man1/ls.1.html) , [cd](https://man7.org/linux/man-pages/man1/cd.1p.html) , [cat](https://man7.org/linux/man-pages/man1/cat.1.html) , [file](https://man7.org/linux/man-pages/man1/file.1.html) , [du](https://man7.org/linux/man-pages/man1/du.1.html) , [find](https://man7.org/linux/man-pages/man1/find.1.html)

## Helpful Reading Material

- [Google Search for “spaces in filename”](https://www.google.com/search?q=spaces+in+filename)
## Solution

The same thing with the previous level, we cannot just simply use `cat` to print the contents of the file `spaces in this filename`. If we type the filename as is, it will take it as if they are different files. 
```
bandit2@bandit:~$ cat spaces in this filename
cat: spaces: No such file or directory
cat: in: No such file or directory
cat: this: No such file or directory
cat: filename: No such file or directory
```

One solution to this is just using `tab` to auto-complete the filename and it would give us the proper syntax to read the file. Using `\` to break the spaces. 
```
bandit2@bandit:~$ cat spaces\ in\ this\ filename 
aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG
```

Another way is to use quotations to denote that this is one whole string for the filename.
```
bandit2@bandit:~$ cat "spaces in this filename"
aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG
```

