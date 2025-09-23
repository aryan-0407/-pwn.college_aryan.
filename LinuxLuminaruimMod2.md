# Pondering Paths
  ## The Root

Alright, so the filesystem starts at /. Under that, there are a whole mess of other directories, configuration files, programs, and, most importantly, flags. In this level, we've added a program right in /, called pwn, that will give you the flag. All you need to do for this level is to invoke this program!

You can invoke a program by providing its path on the command line. In this case, you'll be giving the exact path, starting from /, so the path would be /pwn. This style of path, one that starts with the root directory, is referred to as an "absolute path".

Start the challenge, launch a terminal, invoke the pwn program using its absolute path, and Capture that Flag! Good luck!
  ### Solve
  **Flag:** `pwn.college{AFT_iHgMt64nhu9S8PN-y9P6aNg.QX4cTO0wiNyAzNzEzW}`  
```
Connected!
hacker@paths~the-root:~$ cd
hacker@paths~the-root:~$ pwn
It looks like you invoked 'pwn' instead of the absolute path ('/pwn'). You'll
learn more about how this is different later, but suffice it to say: you ran
the wrong thing. Use the absolute path, instead!
hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{AFT_iHgMt64nhu9S8PN-y9P6aNg.QX4cTO0wiNyAzNzEzW}
hacker@paths~the-root:~$


```


### New Learnings
I learned that tor getting absolute path you must start with forward slashes. I made that mistske here so ill remember it in further tasks.
