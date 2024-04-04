# Krypton Solutions and Writeups

Welcome to the Krypton directory! Here, you'll discover my solutions and insights for each level of the OverTheWire Krypton wargame.

Dive in by tackling the initial challenge of '[Krypton Level 0 → Level 1](#krypton-level-0--level-1)' and advance through the remaining stages. See how I've enhanced my understanding of **cryptographic techniques** and sharpened my skills in **cryptanalysis** as I navigated through these challenges.

## Disclaimer
_The insights and solutions presented in this directory are designed exclusively for educational use. They are offered to assist in grasping and comprehending cybersecurity concepts associated with cryptographic methods and cryptanalysis. Engaging in any unauthorized or unethical activities using these solutions is highly discouraged._ 

## Contents

| Krypton Level 0 → Level 7    |
|---------------------------|
| [Krypton Level 0 → Level 1](#krypton-level-0--level-1)     |
| [Krypton Level 1 → Level 2](#krypton-level-1--level-2)     |
| [Krypton Level 2 → Level 3](#krypton-level-2--level-3)     |
| [Krypton Level 3 → Level 4](#krypton-level-3--level-4)     |
| [Krypton Level 4 → Level 5](#krypton-level-4--level-5)     |
| [Krypton Level 5 → Level 6](#krypton-level-5--level-6)     |
| [Krypton Level 6 → Level 7](#krypton-level-6--level-7)     

# Krypton Level 0 → Level 1

## Level Info

Welcome to Krypton! The first level is easy. The following string encodes the password using Base64:

```
S1JZUFRPTklTR1JFQVQ=
```

Use this password to log in to krypton.labs.overthewire.org with username krypton1 using SSH on port 2231. You can find the files for other levels in /krypton/

## Solution

What we know : 

- We are given the password which is encoded in base64.

We can decode this easily using `base64 -d`
```bash
└─$ echo S1JZUFRPTklTR1JFQVQ= > krypton1
└─$ cat krypton1 | base64 -d            
KRYPTONISGREAT
```
# Krypton Level 1 → Level 2

## Level Info

The password for level 2 is in the file ‘krypton2’. It is ‘encrypted’ using a simple rotation. It is also in non-standard ciphertext format. When using alpha characters for cipher text it is normal to group the letters into 5 letter clusters, regardless of word boundaries. This helps obfuscate any patterns. This file has kept the plain text word boundaries and carried them to the cipher text. Enjoy!

## Solution

What we know : 
- Password for level 2 is in file `krypton2` and is encrypted
- Simple rotation

Since there is nothing in our home directory, we must first find where this file is located. Using `find / | grep krypton2`. Since there are a lot of errors when running this, we will filter these out using `2>/dev/null`
```
krypton1@bandit:~$ find / 2>/dev/null | grep krypton2
/etc/krypton_pass/krypton2
/home/krypton2
/home/krypton2/.profile
/home/krypton2/.bashrc
/home/krypton2/.bash_logout
/krypton/krypton2
/krypton/krypton2/README
/krypton/krypton2/krypton3
/krypton/krypton2/encrypt
/krypton/krypton2/keyfile.dat
/krypton/krypton1/krypton2
```

We see the file and it is in `/krypton/krypton1/`

Going into that folder and checking the files
```
krypton1@bandit:~$ cd /krypton/krypton1
krypton1@bandit:/krypton/krypton1$ ls
krypton2  README
```

```
krypton1@bandit:/krypton/krypton1$ cat krypton2 
YRIRY GJB CNFFJBEQ EBGGRA
```
This is encoded by a simple rotation but we don't know what, maybe the readme will give us clues.

Printing README
```
krypton1@bandit:/krypton/krypton1$ cat README 
Welcome to Krypton!

This game is intended to give hands on experience with cryptography
and cryptanalysis.  The levels progress from classic ciphers, to modern,
easy to harder.

Although there are excellent public tools, like cryptool,to perform
the simple analysis, we strongly encourage you to try and do these
without them for now.  We will use them in later excercises.

** Please try these levels without cryptool first **


The first level is easy.  The password for level 2 is in the file 
'krypton2'.  It is 'encrypted' using a simple rotation called ROT13.  
It is also in non-standard ciphertext format.  When using alpha characters for
cipher text it is normal to group the letters into 5 letter clusters, 
regardless of word boundaries.  This helps obfuscate any patterns.

This file has kept the plain text word boundaries and carried them to
the cipher text.

Enjoy!
```

We now know that it is encrypted using ROT13
Since this is a common encryption, there are a lot of decoders online.
But we can do it in the shell with `tr 'A-Za-z' 'N-ZA-Mn-za-m'`
```
krypton1@bandit:/krypton/krypton1$ cat krypton2 | tr 'A-Za-z' 'N-ZA-Mn-za-m'
LEVEL TWO PASSWORD ROTTEN
```

