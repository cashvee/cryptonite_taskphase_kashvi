### THINGS I'D LIKE TO COME BACK TO REVIEW AGAIN: PROCESS SUBSTITUTION - LAST TWO CHALLENGES.

## 1: REDIRECTING OUTPUT 
**overview**: redirect stdout to files - using the **>** character
echo - to display 

**COMMANDS:**
`hacker@piping~redirecting-output:~$ echo PWN>COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your`

**flag:** pwn.college{c8oHGnZHnJHMWQj4ydebWrhtOAA.dRjN1QDL0UTO0czW}

## 2: REDIRECTING MORE OUTPUT
**OVERVIEW:** redirect the output of any command

**COMMAND(s):**
`hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
hacker@piping~redirecting-more-output:~$ cat myflag
[FLAG] Here is your flag:`

**FLAG:** pwn.college{QhMXUl0t_dK-DdQ-CUru7tZ4Z8C.dVjN1QDL0UTO0czW}`

## 3: APPENDING OUTPUT
**OVERVIEW:**  to make all output keep appending to the same file; which can get deleted if we use **>**
So, we use **>>**

**COMMAND(S):**
`hacker@piping~appending-output:~$ /challenge/run>>~/the-flag
hacker@piping~appending-output:~$ cat the-flag
 |
\|/ This is the first half:
 v
pwn.college{Ag-s-xb790nc0YpPP0XMOTfQxO-.ddDM5QDL0UTO0czW}
                              ^
     that is the second half /|\`
     
**FLAG:** pwn.college{Ag-s-xb790nc0YpPP0XMOTfQxO-.ddDM5QDL0UTO0czW}

## 4: REDIRECTING ERRORS
**OVERVIEW**: _File Descriptor numbers_
FD 0: Standard Input
FD 1: Standard Output
FD 2: Standard Error

**COMMANDS:**
`hacker@piping~redirecting-errors:~$ /challenge/run>myflag2>instructions
hacker@piping~redirecting-errors:~$ cat instructions
hacker@piping~redirecting-errors:~$ cat myflag
[FLAG] Here is your flag:`

**FLAG:** pwn.college{UfebqIoTt3RidOGE1j5i22iQjnI.ddjN1QDL0UTO0czW}

## 5: REDIRECTING INPUT 
**OVERVIEW:** redirect input to programs; done using **<**

**COMMANDS**
``hacker@piping~redirecting-input:~$ echo COLLEGE>PWN
hacker@piping~redirecting-input:~$ cat PWNCOLLEGE
hacker@piping~redirecting-input:~$ /challenge/run<PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read
the value 'COLLEGE' out of it!
Here is your flag:``

**FLAG:**
pwn.college{wBKKrKqNcsYGb2X2GKNo188D-4h.dBzN1QDL0UTO0czW}

## 6: Grepping Stored Results: 
**OVERVIEW**: search through the resulting file after running commands and redirecting their output

**COMMANDS:**
` /challenge/run>/tmp/data.txt`
`cat /tmp/data.txt | grep pwn.college `

**FLAG:** pwn.college{ALtqRkA9obRcOzGfrG-lnmW_WCc.dhTM4QDL0UTO0czW}

## 7: Grepping live output
**OVERVIEW**: Standard output from the command to the left of the pipe will be connected to (piped into) the standard input of the command to the right of the pipe. (**|**)

**COMMANDS**
`hacker@piping~grepping-live-output:~$ /challenge/run | grep pwn.college`

**FLAG:**
pwn.college{I4d6kewhpMKgL9so43EM-qNep5D.dlTM4QDL0UTO0czW}

## 8: Grepping errors
**OVERVIEW:** grep through errors directly; **>&** operator: redirects a file descriptor to another file descriptor; 

**COMMANDS:** `/challenge/run 2>& 1 | grep pwn.college`

**FLAG:**
pwn.college{8oiHrZ9MP3l5iPdWiLV16hm-zDb.dVDM5QDL0UTO0czW}

## 9: Duplicating piped data with tee
**OVERVIEW**: Tee command: It copies command output to both a file and the next command in the pipeline.
/challenge/college command takes the output produced by /challenge/pwn (intercepted and saved by tee in pwn_output) and uses it as its input. It then processes that input (checking if my secret code is correct) 
and provides the flag.

**COMMANDS:** 
**used the tee command to see (intercept) the output from /challenge/pwn and save it in a file (pwn_output)**
`hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee pwn_output | /challenge/college
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
Great job! Here is your flag:`

**FLAG:**
pwn.college{Q4vS2S2bVhD5yAb1UoSWaJPpdTP.dFjM5QDL0UTO0czW}

## 10: Writing to multiple programs
**OVERVIEW:** 
output of /challenge/hack is duplicated using tee and simultaneously sent as input to both /challenge/the and /challenge/planet. 
This is done using process substitution.

**COMMANDS:** 
`hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >(/challenge/the) >(/challenge/planet)
This secret data must directly and simultaneously make it to /challenge/the and
/challenge/planet. Don't try to copy-paste it; it changes too fast.
25455192112891825604
Congratulations, you have duplicated data into the input of two programs! Here
is your flag:`

**FLAG:**
pwn.college{wsV1mLiufER_79RFYvHBMS6J_JM.dBDO0UDL0UTO0czW}

## 11: Split-piping stderr and stdout
**OVERVIEW:** /challenge/hack sends its stderr to /challenge/the and its stdout (>) to /challenge/planet using process substitution 

**COMMANDS:**
`hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack 2> >(/challenge/the) > >(/challenge/planet)
Congratulations, you have learned a redirection technique that even experts
struggle with! Here is your flag:`

**FLAG:**
pwn.college{0wsRpBPl1Aayq1-7J8G2vQgbFbz.dFDNwYDL0UTO0czW}
