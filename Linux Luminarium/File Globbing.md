## 1: Matching with *
**OVERVIEW:** When it encounters a * character in any argument, the shell will treat it as "wildcard" and try to replace that argument with any files that match the pattern.

**commands:**
`hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ ./run
You ran me with the working directory of /challenge! Here is your flag:`

**flag:** pwn.college{UTntTJ7j-P51xfTnHdZQQObXFT7.dFjM4QDL0UTO0czW}

## 2: Matching with ? 
**OVERVIEW:** When it encounters a ? character in any argument, the shell will treat it as **single-character** wildcard.

**commands:**
`hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ ./run
You ran me with the working directory of /challenge! Here is your flag:`

**flag:** pwn.college{M8c0_3jEUbcsn_6YxPt2Yy_K0WS.dJjM4QDL0UTO0czW}

## 3: Matching with []
**OVERVIEW:** Instead of matching any character, [] is a wildcard for some subset of potential characters, specified within the brackets.

**commands:**
`hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[absh]
You got it! Here is your flag!`

**flag:** pwn.college{cqYTYRuQbvYsuRpPt_AMU39lAN3.dNjM4QDL0UTO0czW}

## 4: Matching paths with []
**OVERVIEW:** expand entire paths with the globbed arguments

**commands:**
`hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[bash]
You got it! Here is your flag!`

**flag:** pwn.college{8cdK4DuBtNrgk0vdZHQFs5XO44y.dRjM4QDL0UTO0czW}

## 5: Mixing globs
**OVERVIEW:** 
1- change directory to /challenge/files
2- list all files in the directory
3- challenging, educational, and pwning are the only files that begin with c, e, p 
4- run /challenge/run [cep]* in the terminal

**commands:**
`hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*
You got it! Here is your flag!`

**flag:** pwn.college{QtVwQNoNUqXiBcFEpFlvIHmbMlR.dVjM4QDL0UTO0czW}

## 6: Exclusionary globbing
**OVERVIEW:** to filter out files in a glob; **!** or **^** used.

**commands:**
`hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [!pwn]*
You got it! Here is your flag!`

**flag:** pwn.college{MK85Pb1rHQTvfIqFUlyza0M5g2J.dZjM4QDL0UTO0czW}
