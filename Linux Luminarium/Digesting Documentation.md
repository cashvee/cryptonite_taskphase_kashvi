## Challenge 1: Learning from Documentation
**Overview:** 

**Command(s)**: `hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:`

**Flag:** pwn.college{c5I1Pq-jUtvJfjdYxRhoGWEEBHh.dRjM5QDL0UTO0czW}

## Challenge 2: Learning Complex Usage
**Overview:** The argument to the --printfile argument is the path of the flag to read.

**Command(s)**: `hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /flag
Correct argument! Here is the /flag file:`

**Flag:** pwn.college{okcyWx2MdlgGTxc8s1oVDJHFXun.dVjM5QDL0UTO0czW}

## Challenge 3: Reading Manuals
**Overview:** This level introduces the man command. 
man is short for manual, and will display (if available) the manual of the command you pass as an argument.
hen you're done reading the manpage, you can hit q to quit.

**Command(s):**
`hacker@man~reading-manuals:~$ /challenge/challenge --froskj 564
Correct usage! Your flag: `

**Flag:** pwn.college{QU5PK6fTYETr4YKoUX2skjWUZVd.dRTM4QDL0UTO0czW}

## Challenge 4: Searching Manuals
**Overview:** You can scroll man pages with the arrow keys (and PgUp/PgDn) and search with /.
After searching, you can hit n to go to the next result and N to go to the previous result. 
Instead of /, you can use ? to search backwards!
Find the option that will give you the flag by reading the challenge man page.

ran man challenge in the terminal to read the manual of the challenge command
used /flag to search for flag in the manual
found the following information in the DESCRIPTION section:
--igkwzwe This argument will give you the flag!

**Command(s):**
`hacker@man~searching-manuals:~$ /challenge/challenge --igkwzwe
Initializing...
Correct usage! Your flag: `

**Flag:** pwn.college{gqQCx0D5LldYRzEwC1WJsJ_A6z1.dVTM4QDL0UTO0czW}

## Challenge 5: Searching For Manuals
**Overview:** 
ran: man -k challenge -> gave a list of all man pages related to the keyword "challenge"
`hacker@man~searching-for-manuals:~$ man -k challenge
qfwxiopxwq (1)       - print the flag!`
`hacker@man~searching-for-manuals:~$ /challenge/challenge  --qfwxio 929
Correct usage! Your flag:`

**Command(s):**
`hacker@man~searching-manuals:~$ /challenge/challenge --igkwzwe
Initializing...
Correct usage! Your flag: `

**Flag:** pwn.college{EqIf9wK_2SxKFNiE9opSKxwXqQ2.dZTM4QDL0UTO0czW}

## Challenge 6: HELPFUL PROGRAMS
**OVERVIEW:** 

**COMMANDS:**
`/challenge/challenge --help 
hacker@man~helpful-programs:~$ /challenge/challenge -p
The secret value is: 494
hacker@man~helpful-programs:~$ /challenge/challenge -g 494
Correct usage! Your flag:`

**FLAG**
pwn.college{UDFJhwnMBpzDbNh4cNI9Af-v_mJ.ddjM4QDL0UTO0czW}

## Challenge 7: builtins 
**Overview:** Builtins are invoked just like commands, but the shell handles them internally instead of launching other programs.

**Command(s):**
`hacker@man~help-for-builtins:~$ help challenge
hacker@man~help-for-builtins:~$ cd /challenge
hacker@man~help-for-builtins:/challenge$ challenge --secret 8ZeDaMpX
Correct! Here is your flag!`

**Flag:** pwn.college{8ZeDaMpXzSKEGQuus4nb5u6qzRf.dRTM5QDL0UTO0czW}

