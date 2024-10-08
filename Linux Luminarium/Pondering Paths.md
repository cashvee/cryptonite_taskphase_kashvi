(Apologies I was unaware of flag submission and thus, flags are only noted down starting the last challenge of this module aka "home sweet home".)

## Overview of the module: Basics of Linux file paths

A path from the root of the filesystem starts with /. 
And two kinds of paths were covered namely - absolute and relative. 

for me, all of the challenges were not much of hassles to overcome. But the last one, "Home Sweet Home" took me a little longer than the other ones.

### "Home Sweet Home"
**Flag** : pwn.college{Ie2TbpTBdxqM0J3XMxQ-P6pPHcp.dNzM4QDL0UTO0czW}

**Description:**
In this challenge, /challenge/run will write a copy of the flag to any file you specify as an argument on the commandline, with these constraints:
1) Your argument must be an absolute path.
2) The path must be inside your home directory.
3) Before expansion, your argument must be three characters or less.

**Learnt:** using the cat command to read out files 

**Issue faced**: 

-I wanted to create a file named **a**, however, there was a directory named a in the home directory, which caused the program to fail initially. 

-proceeded to remove the directory and created a file named **a** instead.

-After that, the challenge program successfully wrote the flag to the file ~/a.

-Then used **cat** to read the flag from the file, confirming the flag.
