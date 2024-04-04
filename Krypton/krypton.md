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


