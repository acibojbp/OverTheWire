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

# Krypton Level 2 → Level 3

## Level Info

ROT13 is a simple substitution cipher.

Substitution ciphers are a simple replacement algorithm. In this example of a substitution cipher, we will explore a ‘monoalphebetic’ cipher. Monoalphebetic means, literally, “one alphabet” and you will see why.

This level contains an old form of cipher called a ‘Caesar Cipher’. A Caesar cipher shifts the alphabet by a set number. For example:

```
plain:  a b c d e f g h i j k ...
cipher: G H I J K L M N O P Q ...
```

In this example, the letter ‘a’ in plaintext is replaced by a ‘G’ in the ciphertext so, for example, the plaintext ‘bad’ becomes ‘HGJ’ in ciphertext.

The password for level 3 is in the file krypton3. It is in 5 letter group ciphertext. It is encrypted with a Caesar Cipher. Without any further information, this cipher text may be difficult to break. You do not have direct access to the key, however you do have access to a program that will encrypt anything you wish to give it using the key. If you think logically, this is completely easy.

One shot can solve it!

Have fun.

Additional Information:

The `encrypt` binary will look for the keyfile in your current working directory. Therefore, it might be best to create a working direcory in /tmp and in there a link to the keyfile. As the `encrypt` binary runs setuid `krypton3`, you also need to give `krypton3` access to your working directory.

Here is an example:

```
krypton2@melinda:~$ mktemp -d
/tmp/tmp.Wf2OnCpCDQ
krypton2@melinda:~$ cd /tmp/tmp.Wf2OnCpCDQ
krypton2@melinda:/tmp/tmp.Wf2OnCpCDQ$ ln -s /krypton/krypton2/keyfile.dat
krypton2@melinda:/tmp/tmp.Wf2OnCpCDQ$ ls
keyfile.dat
krypton2@melinda:/tmp/tmp.Wf2OnCpCDQ$ chmod 777 .
krypton2@melinda:/tmp/tmp.Wf2OnCpCDQ$ /krypton/krypton2/encrypt /etc/issue
krypton2@melinda:/tmp/tmp.Wf2OnCpCDQ$ ls
ciphertext  keyfile.dat
```

## Solution

What we know : 
- Password is in krypton3 file
- Encrypted in unknown number of rotations, Caesar's cipher
- Encrypt binary will encrypt a message for us using the keyfile.dat

```
krypton2@bandit:/$ cd /krypton/krypton2
krypton2@bandit:/krypton/krypton2$ ls
encrypt  keyfile.dat  krypton3  README
```

We can see a few files, one of which is our password.
However, we even though we can read it, we don't understand it, as it is encoded in a Caesar's cipher and we don't know how much it is rotated.
```
krypton2@bandit:/krypton/krypton2$ cat krypton3 
OMQEMDUEQMEK
```

The readme file has the same content as that on the website.

To solve this, we must first know what is the number of rotations used.
We are given the encrypt binary which will encrypt a file we give it using the same key used on krypton3.
We need to create a sample text, for us to decipher the key. Since we cannot create a file in this folder we need to create a temp folder and link `keyfile.dat`
```
krypton2@bandit:~$ cd $(mktemp -d)
krypton2@bandit:/tmp/tmp.WovhpxATwY$ ln -s /krypton/krypton2/keyfile.dat 
krypton2@bandit:/tmp/tmp.WovhpxATwY$ ls
keyfile.dat
```

We can now create a basic file
```
krypton2@bandit:/tmp/tmp.WovhpxATwY$ echo ABCD > rot.txt
krypton2@bandit:/tmp/tmp.WovhpxATwY$ cat rot.txt
ABCD
```

Since the encrypt binary is owned by krypton3, it is important that krypton3 has the proper permissions to our temp folder. We can do this using `chmod`
```
krypton2@bandit:/tmp/tmp.WovhpxATwY$ chmod 777 .
krypton2@bandit:/tmp/tmp.WovhpxATwY$ ls -la
total 408
drwsrwsrwx   2 krypton2 krypton2   4096 Mar  2 06:35 .
drwxrwx-wt 140 root     root     405504 Mar  2 06:36 ..
```

We can now use the encrypt binary to encrypt our sample text and we will figure out the key
```
krypton2@bandit:/tmp/tmp.WovhpxATwY$ /krypton/krypton2/encrypt rot.txt
krypton2@bandit:/tmp/tmp.WovhpxATwY$ ls
ciphertext  keyfile.dat  rot.txt
krypton2@bandit:/tmp/tmp.WovhpxATwY$ cat ciphertext 
MNOP
```

It shows that ABCD maps to MNOP, which means that the key is 12. Since this is the encryption key we need to convert it to do decryption, which is done the following way 26 -12 = 14.
We can now use the method on the previous level to get our password.

```
krypton2@bandit:/tmp/tmp.WovhpxATwY$ cat /krypton/krypton2/krypton3 | tr 'A-Za-z' 'O-ZA-No-za-n'
CAESARISEASY
```


