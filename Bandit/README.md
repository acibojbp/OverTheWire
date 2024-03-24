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

# Bandit Level 3 → Level 4

## Level Goal

The password for the next level is stored in a hidden file in the **inhere** directory.

## Commands you may need to solve this level

[ls](https://man7.org/linux/man-pages/man1/ls.1.html) , [cd](https://man7.org/linux/man-pages/man1/cd.1p.html) , [cat](https://man7.org/linux/man-pages/man1/cat.1.html) , [file](https://man7.org/linux/man-pages/man1/file.1.html) , [du](https://man7.org/linux/man-pages/man1/du.1.html) , [find](https://man7.org/linux/man-pages/man1/find.1.html)

## Solution

In this level, the password is stored inside a hidden file inside the `inhere` directory.
Let's check what is inside the directory using the command `ls`
```
bandit3@bandit:~$ ls
inhere
bandit3@bandit:~$ ls ./inhere
bandit3@bandit:~$ 
```

Because the file is hidden we cannot see it by simply using `ls`, we must add `-a` to view all files including hidden files.
```
bandit3@bandit:~$ ls -a ./inhere
.  ..  .hidden
```

To read the hidden file, we must also specify the path just like the previous levels and we get our password.
```
bandit3@bandit:~$ cat ./inhere/.hidden
2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe
```
# Bandit Level 4 → Level 5

## Level Goal

The password for the next level is stored in the only human-readable file in the **inhere** directory. Tip: if your terminal is messed up, try the “reset” command.

## Commands you may need to solve this level

[ls](https://man7.org/linux/man-pages/man1/ls.1.html) , [cd](https://man7.org/linux/man-pages/man1/cd.1p.html) , [cat](https://man7.org/linux/man-pages/man1/cat.1.html) , [file](https://man7.org/linux/man-pages/man1/file.1.html) , [du](https://man7.org/linux/man-pages/man1/du.1.html) , [find](https://man7.org/linux/man-pages/man1/find.1.html)

## Solution

The password is stored in the only human-readable file
```
bandit4@bandit:~$ ls
inhere
bandit4@bandit:~$ ls ./inhere
-file00  -file02  -file04  -file06  -file08
-file01  -file03  -file05  -file07  -file09
```

Checking one of the files...
```
bandit4@bandit:~$ cd inhere
bandit4@bandit:~/inhere$ cat ./-file00
QRrtZ�i�	�H
                  |��ȧ����^��bandit4@bandit:~/inhere$ 
bandit4@bandit:~/inhere$ 
```
It gives us random binary data

Since there are only 10 files here, we can brute force and look inside each one to get our password.
But what if there are thousands of files and only one is human-readable? 
One procedural way of doing this is by using the `file` command 
```
bandit4@bandit:~/inhere$ file ./*
./-file00: data
./-file01: data
./-file02: data
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data
```

We can also use `grep` to filter out the file which is ASCII. This is if there are a lot of files and its hard to go through looking for the only human-readable. 
```
bandit4@bandit:~/inhere$ file ./* | grep ASCII
./-file07: ASCII text
```
We can see that only `-file07` is ASCII text, and by reading that file...
```
bandit4@bandit:~/inhere$ cat ./-file07
lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR
```

# Bandit Level 5 → Level 6

## Level Goal

The password for the next level is stored in a file somewhere under the **inhere** directory and has all of the following properties:

- human-readable
- 1033 bytes in size
- not executable

## Commands you may need to solve this level

[ls](https://man7.org/linux/man-pages/man1/ls.1.html) , [cd](https://man7.org/linux/man-pages/man1/cd.1p.html) , [cat](https://man7.org/linux/man-pages/man1/cat.1.html) , [file](https://man7.org/linux/man-pages/man1/file.1.html) , [du](https://man7.org/linux/man-pages/man1/du.1.html) , [find](https://man7.org/linux/man-pages/man1/find.1.html)

## Solution

The password is stored somewhere under the `inhere` directory and there are a few conditions for us to know which one of those files has our password.

- human-readable
- 1033 bytes in size
- not executable


Looking through one of the folders, we can see that there are a lot of files inside them.
```
bandit5@bandit:~$ ls
inhere
bandit5@bandit:~$ cd inhere
bandit5@bandit:~/inhere$ ls
maybehere00  maybehere04  maybehere08  maybehere12  maybehere16
maybehere01  maybehere05  maybehere09  maybehere13  maybehere17
maybehere02  maybehere06  maybehere10  maybehere14  maybehere18
maybehere03  maybehere07  maybehere11  maybehere15  maybehere19
bandit5@bandit:~/inhere$ cd maybehere00
bandit5@bandit:~/inhere/maybehere00$ ls
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3
bandit5@bandit:~/inhere/maybehere00$ 
```

To solve this, we can use the command `find` and by reading the `man` pages of find we see that we can add `-size` to specify a file size, and since in the specified properties, it says that the file size is 1033 bytes, we can use this. 
```
-size n[cwbkMG]
              File uses less than, more than or exactly  n  units  of  space,
              rounding up.  The following suffixes can be used:

              `b'    for 512-byte blocks (this is the default if no suffix is
                     used)

              `c'    for bytes

```

Using the command `find` and adding the specific size 1033 bytes denoted by `c` for bytes, we find that there is only one file that has that property. 
```
bandit5@bandit:~/inhere$ find -size 1033c
./maybehere07/.file2
```

And printing out the contents of that file, we find our password.
```
bandit5@bandit:~/inhere$ cat ./maybehere07/.file2
P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU
```

> Note : We used the file size as our identifier since it is the most specific. Using the other parameters, human-readable and not executable still yields a lot of results.

```
find \! -executable
```
> Note :  `\! : Simply means "not"`

```
find -exec file {} \; | grep "ASCII text"
```
> Note :
> `-exec file {} \;` : Executes the file command for each file found by `find`.
> 
> `file {}` : The `{}` is a placeholder for the current file found by `find`.
> 
> `\;` : Indicates the end of the `-exec` command.
> 
> `| grep "ASCII text"`: Pipes the output of the file command to `grep` to filter out only files that contain "ASCII text", which typically denotes human-readable text files.

# Bandit Level 6 → Level 7

## Level Goal

The password for the next level is stored **somewhere on the server** and has all of the following properties:

- owned by user bandit7
- owned by group bandit6
- 33 bytes in size

## Commands you may need to solve this level

[ls](https://man7.org/linux/man-pages/man1/ls.1.html) , [cd](https://man7.org/linux/man-pages/man1/cd.1p.html) , [cat](https://man7.org/linux/man-pages/man1/cat.1.html) , [file](https://man7.org/linux/man-pages/man1/file.1.html) , [du](https://man7.org/linux/man-pages/man1/du.1.html) , [find](https://man7.org/linux/man-pages/man1/find.1.html) , [grep](https://man7.org/linux/man-pages/man1/grep.1.html)


## Solution

To solve this, we can again use the command `find`. Reading the **man** pages, we find that there is an argument that we can use for find to specify user and group. 
```
       -user uname
              File is owned by user uname (numeric user ID allowed).
```
```
   -group gname
              File belongs to group gname (numeric group ID allowed).
```
Using this information and the previous `-size` for the specific size of the file, we can find the file that contains the password.

Since the file is stored **somewhere on the server** this means that we need to use `find /`
```
bandit6@bandit:~$ find /
```
This will search the whole server for every file since we did not specify anything. `Ctrl + C` to stop.

Adding our specific properties, we found our file which contains our password.
```
bandit6@bandit:~$ find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
/var/lib/dpkg/info/bandit7.password
bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password
z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S
```
>I added the `2>/dev/null` since executing this command gives a lot of "Permission denied" errors. This gives us a clean output which we can see is just one file.

The expression 2>/dev/null is a shell redirection operator used in Unix-like operating systems to discard error messages or output. Here's what each part means:

`2>`: This part refers to file descriptor 2, which is the standard error (stderr) stream in Unix-like systems. By default, when a program or command encounters an error, it outputs error messages to the stderr stream.

`/dev/null`: This is a special device file in Unix-like systems that discards all data written to it. It essentially acts as a black hole where any data written to it is discarded and not stored anywhere.

So, when you use `2>/dev/null`, you're redirecting any error messages (file descriptor 2) to `/dev/null`, effectively silencing error output. This can be useful in situations where you don't want to see error messages or when you're only interested in the standard output (stdout) of a command and not its errors.

# Bandit Level 7 → Level 8

## Level Goal

The password for the next level is stored in the file **data.txt** next to the word **millionth**

## Commands you may need to solve this level

[man](https://man7.org/linux/man-pages/man1/man.1.html), grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

## Solution

The password is in the file **data.txt**. If we try and read this file, we can see a lot of possible passwords next to some words. The word are interested in is **millionth**.

We can easily search for this using the command `grep`.
```
bandit7@bandit:~$ ls
data.txt
bandit7@bandit:~$ cat data.txt | grep "millionth"
millionth	TESKZC0XvTetK0S9xNwm25STk5iWrBvP
```

`|`: This is the pipe operator. It takes the output of the command on its left (`cat data.txt` in this case) and feeds it as input to the command on its right (`grep "millionth"`).

`grep "millionth"`: This command is used to search for lines in the input that match a specified pattern. In this case, it searches for lines containing the string **millionth** in the output received from `cat data.txt`.

So, combining all these elements, the code reads the contents of **data.txt** and searches for lines containing the string **millionth**, and then it displays those lines in the output.

# Bandit Level 8 → Level 9

## Level Goal

The password for the next level is stored in the file **data.txt** and is the only line of text that occurs only once

## Commands you may need to solve this level

grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

## Helpful Reading Material

- [Piping and Redirection](https://ryanstutorials.net/linuxtutorial/piping.php)

## Solution

The password to the next level is inside the file **data.txt**. If we look at the contents of that file we see a lot of possible passwords, most of them are repeated. We are interested in the one that occurs only once.

To find this we can use the command `uniq`.
```
NAME
       uniq - report or omit repeated lines

SYNOPSIS
       uniq [OPTION]... [INPUT [OUTPUT]]

DESCRIPTION
       Filter adjacent matching lines from INPUT (or standard input), writing
       to OUTPUT (or standard output).

       With no options, matching lines are merged to the first occurrence.
```
Reading the `man` pages, we learn that `uniq` only looks at adjacent lines and merges the lines to their first occurrence, which means we need to first `sort` **data.txt**.

We can pipe the resulting `sort` into `uniq` and add `-u` to print out only the unique line.
```
   -u, --unique
              only print unique lines
```

```
bandit8@bandit:~$ sort data.txt | uniq -u
EN632PlfYiZbn3PhVK3XOGSlNInNE00t
```

`uniq -u`: This command filters out adjacent duplicate lines from its input. The `-u` option specifies that only unique lines should be displayed, and it suppresses the display of lines that appear more than once consecutively.

# Bandit Level 9 → Level 10

## Level Goal

The password for the next level is stored in the file **data.txt** in one of the few human-readable strings, preceded by several ‘=’ characters.

## Commands you may need to solve this level

grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

## Solution

Password is in **data.txt** and is in one of the few human-readable strings.
Preceded by several '=' characters.
Printing the contents of **data.txt** we see...
```
bandit9@bandit:~$ ls
data.txt
bandit9@bandit:~$ cat data.txt
~��Mk���Axڋ��k��;��Jb��mi��~�]��]㹩�ux��R~&�����4SA&l"����x�	6m�q���bf��s���~n�����n����
            ��~��=�|ڱ|J�<��=��u��ڷV���1�`�;�s��g�M-�2k���h�(��1�o�0;T�}��DE*'3�i,���x�ʤ��iSn3�6E�p:���M���O!�d����tW������]��]4&�7�FR^+�6ư�������#
                                                                   d��w�'q�Ԇ
```

- Using the command `strings` we get the following output
```
bandit9@bandit:~$ strings data.txt
4SA&l"
FR^+
3+2)`
^gjb
zVC&
=2""L(
Qu:	
2$A(
HI\}7 H
3X#9
#0jb
uf`e
x]T========== theG)"
PUb,
```

Its interesting that `strings` converts some of the binary data into human-readable format. We see several '=' characters. But the text following that does not seem to be the password we are looking for. 

 We can try and `grep` the output of this to search for the other '=' characters.
```
bandit9@bandit:~$ strings data.txt | grep =====
x]T========== theG)"
========== passwordk^
========== is
========== G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s
```
The result is all the lines with '=' characters and as we see on one of the lines, is our password.

# Bandit Level 10 → Level 11

## Level Goal

The password for the next level is stored in the file **data.txt**, which contains base64 encoded data

## Commands you may need to solve this level

grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

## Helpful Reading Material

- [Base64 on Wikipedia](https://en.wikipedia.org/wiki/Base64)

## Solution

The password is again inside **data.txt**, however this time the contents are base64 encoded data.
We can see this by printing the file.
```
bandit10@bandit:~$ ls
data.txt
bandit10@bandit:~$ cat data.txt
VGhlIHBhc3N3b3JkIGlzIDZ6UGV6aUxkUjJSS05kTllGTmI2blZDS3pwaGxYSEJNCg==
```

Checking the `man` pages of base64 we see that ,
```
NAME
       base64 - base64 encode/decode data and print to standard output

SYNOPSIS
       base64 [OPTION]... [FILE]

DESCRIPTION
       Base64 encode or decode FILE, or standard input, to standard output.

       With no FILE, or when FILE is -, read standard input.

       Mandatory  arguments  to  long options are mandatory for short options
       too.

       -d, --decode
              decode data
```

We can therefore decode the encoded data using the command `base64 -d`.
```
bandit10@bandit:~$ base64 -d data.txt
The password is 6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM
```

# Bandit Level 11 → Level 12

## Level Goal

The password for the next level is stored in the file **data.txt**, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

## Commands you may need to solve this level

grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

## Helpful Reading Material

- [Rot13 on Wikipedia](https://en.wikipedia.org/wiki/Rot13)

## Solution

The password is again stored inside **data.txt** but this time its encoded in a different encryption method, Rot13, also known as [Caesar cipher](https://en.wikipedia.org/wiki/Caesar_cipher).
```
bandit11@bandit:~$ ls
data.txt
bandit11@bandit:~$ cat data.txt
Gur cnffjbeq vf WIAOOSFzMjXXBC0KoSKBbJ8puQm5lIEi
```
- The command rot13 can be used but in our case it's not installed. And since we do not have install privileges we have to decode this manually. 
```
bandit11@bandit:~$ rot13
Command 'rot13' not found, but can be installed with:
apt install bsdgames  # version 2.17-29, or
apt install hxtools   # version 20211204-1
Ask your administrator to install one of them.
```

According to the Wiki on Rot13, the mapping is as follows.
```
tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

We can then pipe the output of **data.txt** to this and we should get our password.
```
bandit11@bandit:~$ cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
The password is JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv
```

Another easy way to do this without knowing the mapping, since a [Caesar cipher](https://en.wikipedia.org/wiki/Caesar_cipher) is pretty common even if the number is different. We can just search for online decoding tools. An example of which is [Rot13.com](rot13.com) which can decode up to Rot25. Similar websites offer up to greater number of shifts.

# Bandit Level 12 → Level 13

## Level Goal

The password for the next level is stored in the file **data.txt**, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv (read the manpages!)

## Commands you may need to solve this level

grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd, mkdir, cp, mv, file

## Helpful Reading Material

- [Hex dump on Wikipedia](https://en.wikipedia.org/wiki/Hex_dump)

## Solution

The password is stored in the file **data.txt**

**data.txt** is a hexdump which has been repeatedly compressed.

Checking the contents we see..
```
bandit12@bandit:~$ ls
data.txt
bandit12@bandit:~$ cat data.txt | head
00000000: 1f8b 0808 6855 1e65 0203 6461 7461 322e  ....hU.e..data2.
00000010: 6269 6e00 013d 02c2 fd42 5a68 3931 4159  bin..=...BZh91AY
00000020: 2653 5948 1b32 0200 0019 ffff faee cff7  &SYH.2..........
00000030: f6ff e4f7 bfbc ffff bff7 ffb9 39ff 7ffb  ............9...
00000040: bd31 eeff b9fb fbbb b9bf f77f b001 3b2c  .1............;,
00000050: d100 0d03 d200 6868 0d00 0069 a00d 0340  ......hh...i...@
00000060: 1a68 00d0 0d01 a1a0 0001 a680 0003 46d4  .h............F.
00000070: 6434 3234 611a 340d 07a4 c351 068f 5000  d424a.4....Q..P.
00000080: 069a 0680 0000 0006 8006 8da4 681a 6868  ............h.hh
00000090: 0d06 8d00 6834 3400 d07a 9a00 01a0 0341  ....h44..z.....A
```

First we need to make our temp folder. To do this without thinking of a folder name just type in `mktemp -d`.
```
bandit12@bandit:~$ mktemp -d
/tmp/tmp.vg20Qi2LlZ
bandit12@bandit:~$ cd /tmp/tmp.vg20Qi2LlZ
bandit12@bandit:/tmp/tmp.vg20Qi2LlZ$ 
```

We can then copy **data.txt** to this temp folder by typing the following command:
```
bandit12@bandit:/tmp/tmp.vg20Qi2LlZ$ cp ~/data.txt .
bandit12@bandit:/tmp/tmp.vg20Qi2LlZ$ ls
data.txt
```

> Note :
> 
> `cp`: This is the command used to copy files or directories in Unix-like operating systems.
>     
> `~/data.txt`: This specifies the source file to be copied. `~/` represents the user's home directory, and `data.txt` is the name of the file to be copied.
>     
> `.`: This specifies the destination directory. In this case, `.` refers to the current directory, where the user is currently located in the terminal.

Now we can work on the **data.txt** file to get our password. 
Reading the `man` pages of `xxd` which is
```
DESCRIPTION
       xxd creates a hex dump of a given file or standard input.  It can also
       convert a hex dump back to its original binary form.  Like uuencode(1)
       and  uudecode(1) it allows the transmission of binary data in a `mail-
       safe' ASCII representation, but has the advantage of decoding to stan‐
       dard  output.   Moreover, it can be used to perform binary file patch‐
       ing.
```

Reading along we find the option to revert the hexdump. 
```
       -r | -revert
              Reverse operation: convert (or patch) hexdump into binary.   If
              not  writing to stdout, xxd writes into its output file without
              truncating it. Use the combination -r -p to read plain hexadec‐
              imal  dumps  without line number information and without a par‐
              ticular column layout. Additional  Whitespace  and  line-breaks
              are allowed anywhere.
```

Applying this to our file we get...
```
bandit12@bandit:/tmp/tmp.vg20Qi2LlZ$ xxd -r data.txt data
bandit12@bandit:/tmp/tmp.vg20Qi2LlZ$ ls
data  data.txt
bandit12@bandit:/tmp/tmp.vg20Qi2LlZ$ file data
data:     gzip compressed data, was "data2.bin", last modified: Thu Oct  5 06:19:20 2023, max compression, from Unix, original size modulo 2^32 573
```
We now see that it is now a `gzip` compressed data. In order to extract this, we first must append the proper suffix to the file. In this case, `.gz`

> Note : We can also determine that this is in fact a gzip compressed data since the first bytes are 1f8b which is the signature of a gzip compressed data. We can find more about signatures in the Wiki, [list of file signatures]([List of file signatures - Wikipedia](https://en.wikipedia.org/wiki/List_of_file_signatures)).

```
bandit12@bandit:/tmp/tmp.vg20Qi2LlZ$ cat data.txt | head
00000000: 1f8b 0808 6855 1e65 0203 6461 7461 322e  ....hU.e..data2.
00000010: 6269 6e00 013d 02c2 fd42 5a68 3931 4159  bin..=...BZh91AY
00000020: 2653 5948 1b32 0200 0019 ffff faee cff7  &SYH.2..........
00000030: f6ff e4f7 bfbc ffff bff7 ffb9 39ff 7ffb  ............9...
```

We can now decompress this `gzip` compressed data by using `gzip -d`.
```
bandit12@bandit:/tmp/tmp.vg20Qi2LlZ$ mv data data.gz
bandit12@bandit:/tmp/tmp.vg20Qi2LlZ$ ls
data.gz  data.txt
bandit12@bandit:/tmp/tmp.vg20Qi2LlZ$ gzip -d data.gz
bandit12@bandit:/tmp/tmp.vg20Qi2LlZ$ ls
data  data.txt
bandit12@bandit:/tmp/tmp.vg20Qi2LlZ$ cat data | head
�h44�z��A����@=�h4hh������hd�����1����������;,�
�����2�3d*58�~  �S�ZP^��luY��Br$�FP!%�s��h�?�)[=�h��O(B��2A���)�tZc��:�pã)�A�ˈ�0���΅A�yjeϢx,�(����z�E�+"�2�/�-��e"���^����t�j���$�d�@�dJơ'7\���$��m1c��#>�aԽ�EV��F��OCӐc@M�C���]��Y2^h8���D=��~	O�I��NDpF�+�|b#Jv
```


Again using the `file` command, we can now tell that the extracted data is a `bzip2` compressed data.
```
bandit12@bandit:/tmp/tmp.vg20Qi2LlZ$ file data
data: bzip2 compressed data, block size = 900k
```

We can also tell this with the signature if we convert it to a hexdump using `xxd`. The signature of a `bzip2` compressed data is **42 5A 68** which we can clearly see as the starting bytes.
I prefer the `file` command since it would be hard to memorize all the file signatures of every file. Using the `file` command just gives us what type of file it is. 
```
/tmp/tmp.vg20Qi2LlZ$ xxd data | head
00000000: 425a 6839 3141 5926 5359 481b 3202 0000  BZh91AY&SYH.2...
00000010: 19ff fffa eecf f7f6 ffe4 f7bf bcff ffbf  ................
00000020: f7ff b939 ff7f fbbd 31ee ffb9 fbfb bbb9  ...9....1.......
00000030: bff7 7fb0 013b 2cd1 000d 03d2 0068 680d  .....;,......hh.
```

`Bzip2` compressed data does not need to have the proper suffix appended. We can decompress this using the same option `-d`.
```
bandit12@bandit:/tmp/tmp.vg20Qi2LlZ$ bzip2 -d data
bzip2: Can't guess original name for data -- using data.out
```

We now see that the output of the `bzip2` decompression is another `gzip` file.
```
bandit12@bandit:/tmp/tmp.vg20Qi2LlZ$ ls
data.out  data.txt
bandit12@bandit:/tmp/tmp.vg20Qi2LlZ$ file data.out
data.out: gzip compressed data, was "data4.bin", last modified: Thu Oct  5 06:19:20 2023, max compression, from Unix, original size modulo 2^32 20480
```

Appending the suffix and decompressing it we find that the extracted file is 
```
bandit12@bandit:/tmp/tmp.vg20Qi2LlZ$ mv data.out data.gz
bandit12@bandit:/tmp/tmp.vg20Qi2LlZ$ gzip -dv data.gz
data.gz:	 98.0% -- replaced with data
bandit12@bandit:/tmp/tmp.vg20Qi2LlZ$ ls
data  data.txt
bandit12@bandit:/tmp/tmp.vg20Qi2LlZ$ file data
data: POSIX tar archive (GNU)
bandit12@bandit:/tmp/tmp.vg20Qi2LlZ$ 
```

We can now see that the extracted data is a tar archive. We can decompress this using `tar -xvf`

> Note : 
> - `tar`: This is the command-line utility used for archiving files and extracting them from archives. It stands for Tape ARchiver.
>     
> - `-x`: This option tells `tar` to extract files from the archive.
>     
> - `-v`: This option stands for "verbose." When used, `tar` displays the names of the files it is extracting while it is working.
>     
> - `-f`: This option is used to specify the name of the archive file. In the command `tar -xvf data`, the archive file is named `data`.

```
bandit12@bandit:/tmp/tmp.vg20Qi2LlZ$ tar -xvf data
data5.bin
bandit12@bandit:/tmp/tmp.vg20Qi2LlZ$ file data5.bin
data5.bin: POSIX tar archive (GNU)
```

```
bandit12@bandit:/tmp/tmp.vg20Qi2LlZ$ tar -xvf data5.bin
data6.bin
bandit12@bandit:/tmp/tmp.vg20Qi2LlZ$ file data6.bin
data6.bin: bzip2 compressed data, block size = 900k
```

We decompressed it twice and now we are back with `bzip2`.
Using the same method, after a couple more extracts we finally get an ASCII text.
```
bandit12@bandit:/tmp/tmp.vg20Qi2LlZ$ bzip2 -d data6.bin
bzip2: Can't guess original name for data6.bin -- using data6.bin.out
bandit12@bandit:/tmp/tmp.vg20Qi2LlZ$ file data6.bin.out
data6.bin.out: POSIX tar archive (GNU)
```

```
bandit12@bandit:/tmp/tmp.vg20Qi2LlZ$ tar -xvf data6.bin.out
data8.bin
bandit12@bandit:/tmp/tmp.vg20Qi2LlZ$ file data8.bin
data8.bin: gzip compressed data, was "data9.bin", last modified: Thu Oct  5 06:19:20 2023, max compression, from Unix, original size modulo 2^32 49
```

```
bandit12@bandit:/tmp/tmp.vg20Qi2LlZ$ mv data8.bin data8.gz
bandit12@bandit:/tmp/tmp.vg20Qi2LlZ$ gzip -d data8.gz
bandit12@bandit:/tmp/tmp.vg20Qi2LlZ$ file data8
data8: ASCII text
```

Printing the contents of **data8** we get our password.
```
bandit12@bandit:/tmp/tmp.vg20Qi2LlZ$ cat data8
The password is wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw
```
# Bandit Level 13 → Level 14

## Level Goal

The password for the next level is stored in **/etc/bandit_pass/bandit14 and can only be read by user bandit14**. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. **Note:** **localhost** is a hostname that refers to the machine you are working on

## Commands you may need to solve this level

ssh, telnet, nc, openssl, s_client, nmap

## Helpful Reading Material

- [SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

## Solution

What we know:
- The password is stored in /etc/bandit_pass/bandit14
- Can only be read by user bandit14
- We get a private ssh key

Checking the home directory for this private ssh key..
```
bandit13@bandit:~$ ls
sshkey.private
bandit13@bandit:~$ cat sshkey.private | head
-----BEGIN RSA PRIVATE KEY-----
MIIEpAIBAAKCAQEAxkkOE83W2cOT7IWhFc9aPaaQmQDdgzuXCv+ppZHa++buSkN+
gg0tcr7Fw8NLGa5+Uzec2rEg0WmeevB13AIoYp0MZyETq46t+jk9puNwZwIt9XgB
ZufGtZEwWbFWw/vVLNwOXBe4UWStGRWzgPpEeSv5Tb1VjLZIBdGphTIK22Amz6Zb
ThMsiMnyJafEwJ/T8PQO3myS91vUHEuoOMAzoUID4kN0MEZ3+XahyK0HJVq68KsV
ObefXG1vvA3GAJ29kxJaqvRfgYnqZryWN7w3CHjNU4c/2Jkp+n8L0SnxaNA+WYA7
jiPyTF0is8uzMlYQ4l1Lzh/8/MpvhCQF8r22dwIDAQABAoIBAQC6dWBjhyEOzjeA
```

Reading the `man` pages of `ssh` 
```
     -i identity_file
             Selects a file from which the identity (private key) for public
             key authentication is read.  You can also specify a public key
             file to use the corresponding private key that is loaded in
             ssh-agent(1) when the private key file is not present locally.
             The default is ~/.ssh/id_rsa, ~/.ssh/id_ecdsa,
             ~/.ssh/id_ecdsa_sk, ~/.ssh/id_ed25519, ~/.ssh/id_ed25519_sk and
             ~/.ssh/id_dsa.  Identity files may also be specified on a per-
             host basis in the configuration file.  It is possible to have
             multiple -i options (and multiple identities specified in con‐
             figuration files).  If no certificates have been explicitly
             specified by the CertificateFile directive, ssh will also try to
             load certificate information from the filename obtained by ap‐
             pending -cert.pub to identity filenames.
```

We can use the given ssh private key to login to the next level.
Save this to a file

# Bandit Level 14 → Level 15


## Level Goal

The password for the next level can be retrieved by submitting the password of the current level to **port 30000 on localhost**.

## Commands you may need to solve this level

ssh, telnet, nc, openssl, s_client, nmap

## Helpful Reading Material

- [How the Internet works in 5 minutes (YouTube)](https://www.youtube.com/watch?v=7_LPdttKXPc) (Not completely accurate, but good enough for beginners)
- [IP Addresses](http://computer.howstuffworks.com/web-server5.htm)
- [IP Address on Wikipedia](https://en.wikipedia.org/wiki/IP_address)
- [Localhost on Wikipedia](https://en.wikipedia.org/wiki/Localhost)
- [Ports](http://computer.howstuffworks.com/web-server8.htm)
- [Port (computer networking) on Wikipedia](https://en.wikipedia.org/wiki/Port_(computer_networking))


## Solution

What we know:
- The password for the next level can be retrieved by submitting the password of bandit14 to port 30000 on localhost
- To access this level we need to use the given ssh key from the previous level.

```
ssh -i bandit14 bandit14@bandit.labs.overthewire.org -p 2220
                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@         WARNING: UNPROTECTED PRIVATE KEY FILE!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
Permissions 0644 for 'bandit14' are too open.
It is required that your private key files are NOT accessible by others.
This private key will be ignored.
Load key "bandit14": bad permissions
bandit14@bandit.labs.overthewire.org's password: 
```

We get this error because our ssh key file is not private. We have to make it private, so that only we can read the file. We can do this by changing the permissions of the file. Checking the current permissions we see..
```
└─$ ls -l bandit14
-rw-r--r-- 1 kali kali 1679 Feb 26 23:47 bandit14
```

> Note :
> 
> `-rw-r--r--`: This part represents the file permissions. In this case:
> 
> - The first character (`-`) indicates that it is a regular file. If it were a directory, it would show `d`.
> - The next three characters (`rw-`) represent the permissions for the file owner (`kali` in this case). `rw-` means that the owner has read and write permissions but no execute permissions.
> - The next three characters (`r--`) represent the permissions for the group (`kali` in this case). `r--` means that the group has only read permissions.
> - The last three characters (`r--`) represent the permissions for others (users who are neither the owner nor in the group). `r--` means that others also have only read permissions.


We need to make the permissions so that only we (the owner) are able to read and write to it. To do this we can use the command `chmod` to change the permissions.
```
└─$ chmod 600 bandit14
└─$ ls -l bandit14
-rw------- 1 kali kali 1679 Feb 26 23:47 bandit14
```

We can now see that there are no longer any read or write permissions with the group and others.

> Note :
> - The first digit (`6`) represents the permissions for the file owner. The value `6` in octal translates to binary `110`, which means the owner has read and write permissions (because `1` represents read and `1` represents write).
> - The second and third digits (`00`) represent the permissions for the group and others, respectively. Both are set to `0`, meaning they have no permissions (neither read, write, nor execute).

With the proper permissions set to our ssh key file we can now use this to login.
```
└─$ ssh -i bandit14 bandit14@bandit.labs.overthewire.org -p 2220
```

We can get the password for the next level by submitting the password for the current level to localhost port 30000.

We can do this by using the `nc` command, reading the `man` pages we see that..
```
SYNOPSIS
     nc [-46bCDdFhklNnrStUuvZz] [-I length] [-i interval] [-M ttl]
        [-m minttl] [-O length] [-P proxy_username] [-p source_port]
        [-q seconds] [-s sourceaddr] [-T keyword] [-V rtable]
        [-W recvlimit] [-w timeout] [-X proxy_protocol]
        [-x proxy_address[:port]] [destination] [port]

DESCRIPTION
     The nc (or netcat) utility is used for just about anything under the
     sun involving TCP, UDP, or UNIX-domain sockets.  It can open TCP con‐
     nections, send UDP packets, listen on arbitrary TCP and UDP ports, do
     port scanning, and deal with both IPv4 and IPv6.  Unlike telnet(1), nc
     scripts nicely, and separates error messages onto standard error in‐
     stead of sending them to standard output, as telnet(1) does with some.
```

The part we are interested in is the syntax. Our destination is localhost and port is 30000.
Unlike `ssh` we don't need the `-p`. Therefore the full command would be `nc localhost 30000`.
Running this the terminal would then wait for a stnd input (the password). Since we did not give anything it would prompt us back with wrong password.
```
bandit14@bandit:~$ nc localhost 30000
 
Wrong! Please enter the correct current password
****
```

We can get the password of the current level from the information from the previous level. It is stored in **/etc/bandit_pass/bandit14**
```
bandit14@bandit:~$ cat /etc/bandit_pass/bandit14
fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq
```
To make things easier, we can pipe this to `nc` and we should be able to get our password for the next level.
```
bandit14@bandit:~$ cat /etc/bandit_pass/bandit14 | nc localhost 30000
Correct!
jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt
```

# Bandit Level 15 → Level 16

## Level Goal

The password for the next level can be retrieved by submitting the password of the current level to **port 30001 on localhost** using SSL encryption.

**Helpful note: Getting “HEARTBEATING” and “Read R BLOCK”? Use -ign_eof and read the “CONNECTED COMMANDS” section in the manpage. Next to ‘R’ and ‘Q’, the ‘B’ command also works in this version of that command…**

## Commands you may need to solve this level

ssh, telnet, nc, openssl, s_client, nmap

## Helpful Reading Material

- [Secure Socket Layer/Transport Layer Security on Wikipedia](https://en.wikipedia.org/wiki/Secure_Socket_Layer)
- [OpenSSL Cookbook - Testing with OpenSSL](https://www.feistyduck.com/library/openssl-cookbook/online/ch-testing-with-openssl.html)


## Solution

What we know :
- The password can be retrieved by submitting the password of the current level to port 30001 on localhost.
- Must use SSL encryption

We can use `openssl` for this. Reading the `man` pages we see, 

```
SYNOPSIS
       openssl command [ options ... ] [ parameters ... ]

DESCRIPTION
       OpenSSL is a cryptography toolkit implementing the Secure Sockets
       Layer (SSL v2/v3) and Transport Layer Security (TLS v1) network
       protocols and related cryptography standards required by them.

       The openssl program is a command line program for using the various
       cryptography functions of OpenSSL's crypto library from the shell.
       It can be used for

        o  Creation and management of private keys, public keys and parameters
        o  Public key cryptographic operations
        o  Creation of X.509 certificates, CSRs and CRLs
        o  Calculation of Message Digests and Message Authentication Codes
        o  Encryption and Decryption with Ciphers
        o  SSL/TLS Client and Server Tests
        o  Handling of S/MIME signed or encrypted mail
        o  Timestamp requests, generation and verification

       s_client
           This implements a generic SSL/TLS client which can establish a
           transparent connection to a remote server speaking SSL/TLS. It's
           intended for testing purposes only and provides only rudimentary
           interface functionality but internally uses mostly all
           functionality of the OpenSSL ssl library.
```

We use the line `openssl s_client -connect localhost:port`
We can get the password for the current level in **/etc/bandit_pass/bandit15**
Pipe that out to the line above and add `-ign_eof`
```
bandit15@bandit:~$ cat /etc/bandit_pass/bandit15 | openssl s_client -connect localhost:30001 -ign_eof
```

We get the password for the next level
```

    Start Time: 1709257084
    Timeout   : 7200 (sec)
    Verify return code: 10 (certificate has expired)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
Correct!
JQttfApK4SeyHwDlI9SXGR50qclOAil1

closed
```

# Bandit Level 16 → Level 17

## Level Goal

The credentials for the next level can be retrieved by submitting the password of the current level to **a port on localhost in the range 31000 to 32000**. First find out which of these ports have a server listening on them. Then find out which of those speak SSL and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

## Commands you may need to solve this level

ssh, telnet, nc, openssl, s_client, nmap

## Helpful Reading Material

- [Port scanner on Wikipedia](https://en.wikipedia.org/wiki/Port_scanner)

## Solution

What we know :

- Credentials for next level can be retrieved by submitting the password of the current level to a port on localhost in the range of 31000-32000.
- We need to find which port is open and which one is speaking SSL. 
- There is only 1 server that will give the credentials.

For this we first need to know which ports are open in the range given. We can use `nmap` for this. 
Reading the `man` pages,
```
NAME
       nmap - Network exploration tool and security / port scanner

SYNOPSIS
       nmap [Scan Type...] [Options] {target specification}

DESCRIPTION
       Nmap (“Network Mapper”) is an open source tool for network
       exploration and security auditing. It was designed to rapidly scan
       large networks, although it works fine against single hosts. 


		   PORT SPECIFICATION AND SCAN ORDER:
             -p <port ranges>: Only scan specified ports
               Ex: -p22; -p1-65535; -p U:53,111,137,T:21-25,80,139,8080,S:9
             --exclude-ports <port ranges>: Exclude the specified ports from scanning
```

We need to specify a target, in this case its localhost.
Running `nmap` we get, 
```
bandit16@bandit:~$ nmap localhost
Starting Nmap 7.80 ( https://nmap.org ) at 2024-03-01 01:45 UTC
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00011s latency).
Not shown: 995 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
1111/tcp  open  lmsocialserver
1840/tcp  open  netopia-vo2
4321/tcp  open  rwhois
30000/tcp open  ndmps

Nmap done: 1 IP address (1 host up) scanned in 0.08 seconds
```

It did not detect the specified ports, so we need to tell `nmap` to specifically search at this range.
```
bandit16@bandit:~$ nmap localhost -p 31000-32000
Starting Nmap 7.80 ( https://nmap.org ) at 2024-03-01 01:46 UTC
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00015s latency).
Not shown: 996 closed ports
PORT      STATE SERVICE
31046/tcp open  unknown
31518/tcp open  unknown
31691/tcp open  unknown
31790/tcp open  unknown
31960/tcp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 0.11 seconds
```

Since there are only 5 ports, we can try connecting to each of these one by one, but what's the fun in that. There is a way for us to know what port runs what service, using the `-sV`.
```
-sV: Probe open ports to determine service/version info
```

```
bandit16@bandit:~$ nmap -sV localhost -p 31000-32000
Starting Nmap 7.80 ( https://nmap.org ) at 2024-03-01 01:52 UTC
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00011s latency).
Not shown: 996 closed ports
PORT      STATE SERVICE     VERSION
31046/tcp open  echo
31518/tcp open  ssl/echo
31691/tcp open  echo
31790/tcp open  ssl/unknown
31960/tcp open  echo
```

We see that only ports 31518 and 31790 run SSL. Port 31518 only run the echo service. The port we are interested in is port 31790. 
Connecting to port 31790 using `openssl` we get, 
```
bandit16@bandit:~$ cat /etc/bandit_pass/bandit16 | openssl s_client -connect localhost:31790 -ign_eof
```

```
Correct!
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----
```

We get a private key, save this to a file and make sure to change the permissions so that only we can read it. Same as the previous level. 

# Bandit Level 17 → Level 18

## Level Goal

There are 2 files in the homedirectory: **passwords.old and passwords.new**. The password for the next level is in **passwords.new** and is the only line that has been changed between **passwords.old and passwords.new**

**NOTE: if you have solved this level and see ‘Byebye!’ when trying to log into bandit18, this is related to the next level, bandit19**

## Commands you may need to solve this level

cat, grep, ls, diff

## Solution

What we know : 

- The password for the next level is in passwords.new
- It is the only line that has been changed between the two files.

To solve this we can use the command `diff`

Reading the `man` pages,
```
NAME
       diff - compare files line by line

SYNOPSIS
       diff [OPTION]... FILES
```

```
bandit17@bandit:~$ ls
passwords.new  passwords.old
```

```
bandit17@bandit:~$ diff passwords.new passwords.old
42c42
< hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg
---
> p6ggwdNHncnmCNxuAt0KtKVq185ZU7AW
```

> Note : 
> 
> - `42c42`: This line indicates a change between the two files. Specifically:
>     
>     - `42` indicates line number 42 in both files.
>     - `c` indicates a change. This means that the content of line 42 in the first file (`passwords.new`) is different from the content of line 42 in the second file (`passwords.old`).
> - `< hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg`: This line represents the content of line 42 in `passwords.new`. The line starts with `<`, indicating that it's present in the first file (`passwords.new`) but not in the second file.
>     
> - `> p6ggwdNHncnmCNxuAt0KtKVq185ZU7AW`: This line represents the content of line 42 in `passwords.old`. The line starts with `>`, indicating that it's present in the second file (`passwords.old`) but not in the first file.

Therefore the password for the next level is 
```
hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg
```

# Bandit Level 18 → Level 19

## Level Goal

The password for the next level is stored in a file **readme** in the homedirectory. Unfortunately, someone has modified **.bashrc** to log you out when you log in with SSH.

## Commands you may need to solve this level

ssh, ls, cat

```
  Enjoy your stay!

Byebye !
Connection to bandit.labs.overthewire.org closed.
                                                    
```

What we know :

- Someone modified the .bashrc file to log us out immediately when we login
- The password is in a readme file in the homedirectory

Reading the `man` pages of `ssh`
```
     If a command is specified, it will be executed on the remote host in‐
     stead of a login shell.  A complete command line may be specified as
     command, or it may have additional arguments.  If supplied, the argu‐
     ments will be appended to the command, separated by spaces, before it is
     sent to the server to be executed.
```

We don't need shell if we just need to run a few commands, this is especially the case in automated shell scripts. SSH can connect remotely and run commands remotely. 
We can test this out by running a simple command at the end of the `ssh` line in `" "`
```
└─$ sshpass -p `cat bandit18` ssh bandit18@bandit.labs.overthewire.org -p 2220 "ls"        
                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

readme
```

We can see that it shows us the output of our command `ls` which shows that there is indeed a readme file in the home directory.

Let's see if we can print the contents of the readme file, if we can that should give us our password
```
└─$ sshpass -p `cat bandit18` ssh bandit18@bandit.labs.overthewire.org -p 2220 "cat readme" 
                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

awhqfNnAbc1naukrpqDYcF95h7HoMTrC
```

>   We can also use SSH to execute commands. Instead of typing the commands directly, we can use `/bin/bash` to start a bash shell or use the `-t` flag to enable a "pseudo-terminal" on the target machine. This allows us to run `/bin/sh`. It's handy when we need to run several commands because we don't have to keep typing the SSH command and password.

```
└─$ sshpass -p `cat bandit18` ssh bandit18@bandit.labs.overthewire.org -p 2220 /bin/bash

└─$ sshpass -p `cat bandit18` ssh bandit18@bandit.labs.overthewire.org -p 2220 -t /bin/sh 
```


