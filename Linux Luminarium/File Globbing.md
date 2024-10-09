1 -
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ ./run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{UTntTJ7j-P51xfTnHdZQQObXFT7.dFjM4QDL0UTO0czW}

2- 
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ ./run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{M8c0_3jEUbcsn_6YxPt2Yy_K0WS.dJjM4QDL0UTO0czW}

3- 
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[absh]
You got it! Here is your flag!
pwn.college{cqYTYRuQbvYsuRpPt_AMU39lAN3.dNjM4QDL0UTO0czW}

4- 
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[bash]
You got it! Here is your flag!
pwn.college{8cdK4DuBtNrgk0vdZHQFs5XO44y.dRjM4QDL0UTO0czW}

5-
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*
You got it! Here is your flag!
pwn.college{QtVwQNoNUqXiBcFEpFlvIHmbMlR.dVjM4QDL0UTO0czW}

6- 
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [!pwn]*
You got it! Here is your flag!
pwn.college{MK85Pb1rHQTvfIqFUlyza0M5g2J.dZjM4QDL0UTO0czW}
