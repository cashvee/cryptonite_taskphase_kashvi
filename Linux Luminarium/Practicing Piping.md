1- 
`hacker@piping~redirecting-output:~$ echo PWN>COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your
flag:
pwn.college{c8oHGnZHnJHMWQj4ydebWrhtOAA.dRjN1QDL0UTO0czW}`

2- 
`hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
hacker@piping~redirecting-more-output:~$ cat myflag
[FLAG] Here is your flag:
[FLAG] pwn.college{QhMXUl0t_dK-DdQ-CUru7tZ4Z8C.dVjN1QDL0UTO0czW}`

3-
hacker@piping~appending-output:~$ /challenge/run>>~/the-flag
hacker@piping~appending-output:~$ cat the-flag
 |
\|/ This is the first half:
 v
pwn.college{Ag-s-xb790nc0YpPP0XMOTfQxO-.ddDM5QDL0UTO0czW}
                              ^
     that is the second half /|\

4- 
hacker@piping~redirecting-errors:~$ /challenge/run>myflag2>instructions
hacker@piping~redirecting-errors:~$ cat instructions
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{UfebqIoTt3RidOGE1j5i22iQjnI.ddjN1QDL0UTO0czW}

5- 
hacker@piping~redirecting-input:~$ echo COLLEGE>PWN
hacker@piping~redirecting-input:~$ cat PWN
COLLEGE
hacker@piping~redirecting-input:~$ /challenge/run<PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{wBKKrKqNcsYGb2X2GKNo188D-4h.dBzN1QDL0UTO0czW}

6-


7-
hacker@piping~grepping-live-output:~$ /challenge/run | grep pwn.college
pwn.college{I4d6kewhpMKgL9so43EM-qNep5D.dlTM4QDL0UTO0czW}

8-
/challenge/run 2>& 1 | grep pwn.college
pwn.college{8oiHrZ9MP3l5iPdWiLV16hm-zDb.dVDM5QDL0UTO0czW}

9-
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee pwn_output | /challenge/college
Processing...
WARNING: you are overwriting file pwn_output with tee's output...
The input to 'college' does not contain the correct secret code! This code
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the
output of 'pwn' and figure out what the code needs to be.
hacker@piping~duplicating-piped-data-with-tee:~$ cat pwn_output
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "Q4vS2S2b"
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret Q4vS2S2b | /challenge/college
Processing...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{Q4vS2S2bVhD5yAb1UoSWaJPpdTP.dFjM5QDL0UTO0czW}

10-
hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >(/challenge/the) >(/challenge/planet)
This secret data must directly and simultaneously make it to /challenge/the and
/challenge/planet. Don't try to copy-paste it; it changes too fast.
25455192112891825604
Congratulations, you have duplicated data into the input of two programs! Here
is your flag:
pwn.college{wsV1mLiufER_79RFYvHBMS6J_JM.dBDO0UDL0UTO0czW}

11-
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack 2> >(/challenge/the) > >(/challenge/planet)
Congratulations, you have learned a redirection technique that even experts
struggle with! Here is your flag:
pwn.college{0wsRpBPl1Aayq1-7J8G2vQgbFbz.dFDNwYDL0UTO0czW}
