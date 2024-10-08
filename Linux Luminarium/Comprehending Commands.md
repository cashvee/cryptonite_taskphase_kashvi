# COMPREHENDING COMMANDS

## Challenge 1: Cat not the pet, the command!
**Overview:** cat is most often used for reading out files; cat will concatenate multiple files if provided multiple arguments.

**Command(s)**: `hacker@commands~cat-not-the-pet-but-the-command: ~$ cat flag`

**Flag:** pwn.college{USIQeCrk6rkwce2SiRUkdyeEaBv.dFzN1QDL0UTO0czW}

## Challenge 2: Catting absolute paths
**Overview:** specify cat's arguments as absolute paths.

**Command(s)**: `hacker@commands~catting-absolute-paths: ~$ cat /flag`

**Flag:** pwn.college{YDEOp4W7U9-K8PYhNgnlLh5yG77.dlTM5QDL0UTO0czW}

## Challenge 3: Catting absolute paths
**Overview:** You cannot use the 'cd' command in this level, and must retrieve the flag by
absolute path. Plus, hid the flag in a different directory! You can find it
in the file /opt/pwndbg/scripts/flag. Go cat it out **without** cding into that
directory!

**Command(s)**:` hacker@commands~more-catting-practice: ~$ cat /opt/pwndbg/scripts/flag`

**Flag:** pwn.college{0TB4v_5MNCsfZuZTTmmXrjJSzUX.dBjM5QDL0UTO0czW}

## Challenge 4: grepping for a needle in a haystack
**Overview:** grep command to search for the contents we need;

`hacker@dojo:~$ grep SEARCH_STRING /path/to/file`
Invoked like this, grep will search the file for lines of text containing SEARCH_STRING and print them to the console.

**Command(s):** `hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt`

**Flag:** pwn.college{si4Cs3uIKvm5gdoe3W1bTCX9Tb0.ddTM4QDL0UTO0czW} 

## Challenge 5: listing files
**Overview:** `ls` will list files in all the directories provided to it as arguments,
and in the current directory if no arguments are provided; list their contents using the ls command.

**Command(s):** `hacker@commands~listing-files:~$ /challenge/26363-renamed-run-1405
Yahaha, you found me! Here is your flag:`

**Flag:** pwn.college{g12QeFJYL6CFhZwYx06XaAirt9M.dhjM4QDL0UTO0czW}

## Challenge 6: touching files
**Overview:** You can create a new, blank file by touching it with the touch command

**Command(s):** 
`hacker@commands~touching-files:/tmp$ touch pwn
hacker@commands~touching-files:/tmp$ touch pwn college
hacker@commands~touching-files:/$ /challenge/run
Success! Here is your flag:`

**Flag:** pwn.college{8Jy1TMGdwK_qni_FsT2By35a2j6.dBzM4QDL0UTO0czW}

## Challenge 7: Removing files
**Overview:** remove files with the rm command

**Command(s):** 
`hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:`

**Flag:** pwn.college{gOGzeEG3LaQRweyyKLhFDidWIwD.dZTOwUDL0UTO0czW}

## Challenge 8: hidden files
**Overview:**  Linux has a convention where files that start with a . don't show up by default in ls and in a few other contexts.
To view them with ls, you need to invoke ls with the -a flag

**Command(s):** `hacker@commands~hidden-files:/$ ls -a
.   .dockerenv             bin   challenge  etc   lib    lib64   media  nix  proc  run   srv  tmp  var
..  .flag-215902890321110  boot  dev        home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~hidden-files:/$ cat /.flag-215902890321110
pwn.college{cC3FYiKx_SjYZyUXdG65HcTkVdG.dBTN4QDL0UTO0czW}`

**Flag:** pwn.college{cC3FYiKx_SjYZyUXdG65HcTkVdG.dBTN4QDL0UTO0czW}

## Challenge 9: An epic filesystem quest
**Overview:** In this challenge, I have hidden the flag! Here, you will use ls and cat to follow my breadcrumbs and find it! Here's how it'll work:
Your first clue is in /. Head on over there.
Look around with ls. There'll be a file named HINT or CLUE or something along those lines!
cat that file to read the clue!
Depending on what the clue says, head on over to the next directory (or don't!).
Follow the clues to the flag!

**Command(s):** 
TOO MANY

**Flag:** pwn.college{86iE7Vsqa2w4dDGRZKHKvl7jWvu.dljM4QDL0UTO0czW}

## Challenge 10: Making Directories
**Overview:** make directories using the mkdir command

**Command(s):** 
`hacker@commands~making-directories:/tmp$ mkdir pwn
hacker@commands~making-directories:/tmp$ ls
bin  hsperfdata_root  pwn  tmp.XvrUsDZh8M
hacker@commands~making-directories:/tmp$ cd pwn
hacker@commands~making-directories:/tmp/pwn$ touch college
hacker@commands~making-directories:/tmp/pwn$ cd
hacker@commands~making-directories:~$ /challenge/run
Success! Here is your flag:`

**Flag:** pwn.college{I3HAulOwIjh7gzFRShKWYhfR2R8.dFzM4QDL0UTO0czW}

## Challenge 11: Finding files
**Overview:** The find command takes optional arguments describing the search criteria and the search location. 
If you don't specify a search criteria, find matches every file. 
If you don't specify a search location, find uses the current working directory (.)

**Command(s):** 
`hacker@commands~finding-files:~$ find / -name flag`
tried reading each file named flag using the cat command.

**Flag:** pwn.college{c1TGZJS0QsBSvfBcpi8RXc-lXye.dJzM4QDL0UTO0czW}

## Challenge 12: Linking files
**Overview:** Links come in two flavors: hard and soft (also known as symbolic) links. We'll differentiate the two with an analogy:
-A hard link is when you address your appartment using multiple addresses that all lead directly to the same place (e.g., Apt 2 vs Unit 2).
-A soft link is when you move appartments and have the postal service automatically forward your mail from your old place to your new place.

learnt: symlinks
Symbolic links are created with the ln command with the -s argument
Note that the original file path comes before the link path in the command.

**NOTE**: make /home/hacker/not-the-flag point to /flag

**Command(s):** 
`hacker@commands~linking-files:~$ rm /home/hacker/not-the-flag
hacker@commands~linking-files:~$ ln -s /flag /home/hacker/not-the-flag
hacker@commands~linking-files:~$ /challenge/catflag
About to read out the /home/hacker/not-the-flag file!`

**Flag:** pwn.college{4portUhyAK_PNNQLoCScA9xKZAD.dlTM1UDL0UTO0czW}
