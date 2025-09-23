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


  ## Program and absolute paths

Let's explore a slightly more complicated path! Except for in the previous level, challenges in pwn.college are in the challenge directory and the challenge directory is, in turn, right in the root directory (/). The path to the challenge directory is, thus, /challenge. The name of the challenge program in this level is run, and it lives in the /challenge directory. Thus, the path to the run challenge program is /challenge/run.

This challenge again requires you to execute it by invoking its absolute path. You'll want to execute the run file that is in the challenge directory that is, in turn, in the / directory. If you invoke the challenge correctly, it will give you the flag. Good luck!
  ### Solve
  **Flag:** `pwn.college{8Qc2ReCXqdExmZ9xzgQOA2qeqct.QX1QTN0wiNyAzNzEzW}`  
```
Connected!
hacker@paths~program-and-absolute-paths:~$ cd
hacker@paths~program-and-absolute-paths:~$ cd /
hacker@paths~program-and-absolute-paths:/$ cd
hacker@paths~program-and-absolute-paths:~$ cd /challenge/run
bash: cd: /challenge/run: Not a directory
hacker@paths~program-and-absolute-paths:~$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{8Qc2ReCXqdExmZ9xzgQOA2qeqct.QX1QTN0wiNyAzNzEzW}
hacker@paths~program-and-absolute-paths:~$


```


### New Learnings
I learned how to navigate to directories inside directories. Also, to invoke an absolute path i shouldnt use cd, i should just write the path starting with a forward slash. 


  ## Position thy self

The Linux filesystem has tons of directories with tons of files. You can navigate around directories by using the cd (change directory) command and passing a path to it as an argument, as so:

 ```
  hacker@dojo:~$ cd /some/new/directory
hacker@dojo:/some/new/directory$  
```

This affects the "current working directory" of your process (in this case, the bash shell). Each process has a directory in which it's currently hanging out. The reasons for this will become clear later in the module.

As an aside, now you can see what the ~ was in the prompt! It shows the current path that your shell is located at.

This challenge will require you to execute the /challenge/run program from a specific path (which it will tell you). You'll need to cd to that directory before rerunning the challenge program. Good luck!

  ### Solve
  **Flag:** `pwn.college{cNWBWX_fu-AwKTsoOQfXgPsTydy.QX2QTN0wiNyAzNzEzW}`  
```
Connected!
hacker@paths~position-thy-self:~$ cd /challenge
hacker@paths~position-thy-self:/challenge$ cd /run
hacker@paths~position-thy-self:/run$ cd
hacker@paths~position-thy-self:~$ cd /
hacker@paths~position-thy-self:/$ ls
bin   challenge  etc   home  lib32  libx32  mnt  opt   root  sbin  sys  usr
boot  dev        flag  lib   lib64  media   nix  proc  run   srv   tmp  var
hacker@paths~position-thy-self:/$ cd
hacker@paths~position-thy-self:~$ cd challenge/run
bash: cd: challenge/run: No such file or directory
hacker@paths~position-thy-self:~$ /challenge/run
Incorrect...
You are not currently in the /proc/131/fd directory.
Please use the cd utility to change directory appropriately.
hacker@paths~position-thy-self:~$ cd /challenge/run
bash: cd: /challenge/run: Not a directory
hacker@paths~position-thy-self:~$ /proc/131/fd
bash: /proc/131/fd: Is a directory
hacker@paths~position-thy-self:~$ /challenge/run
Incorrect...
You are not currently in the /proc/131/fd directory.
Please use the cd utility to change directory appropriately.
hacker@paths~position-thy-self:~$ cd /proc/131/fd
hacker@paths~position-thy-self:/proc/131/fd$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{cNWBWX_fu-AwKTsoOQfXgPsTydy.QX2QTN0wiNyAzNzEzW}
hacker@paths~position-thy-self:/proc/131/fd$


```


### New Learnings
To solve this problem i first had to invoke the absolute path of run (/challenge/run). It then have me an address(/proc/131/fd). Once i went to that directory i had to run the invoke command which gave me my flag.


   ## Position elsewhere

The Linux filesystem has tons of directories with tons of files. You can navigate around directories by using the cd (change directory) command and passing a path to it as an argument, as so:

 ```
  hacker@dojo:~$ cd /some/new/directory
hacker@dojo:/some/new/directory$  
```

This affects the "current working directory" of your process (in this case, the bash shell). Each process has a directory in which it's currently hanging out. The reasons for this will become clear later in the module.

As an aside, now you can see what the ~ was in the prompt! It shows the current path that your shell is located at.

This challenge will require you to execute the /challenge/run program from a specific path (which it will tell you). You'll need to cd to that directory before rerunning the challenge program. Good luck!

  ### Solve
  **Flag:** `pwn.college{8De72TcqYUZOLVYFrO0fPx7tj5j.QX3QTN0wiNyAzNzEzW}`  
```
Connected!
hacker@paths~position-elsewhere:~$ cd /challenge/run
bash: cd: /challenge/run: Not a directory
hacker@paths~position-elsewhere:~$ cd challenge/run
bash: cd: challenge/run: No such file or directory
hacker@paths~position-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /tmp directory.
Please use the cd utility to change directory appropriately.
hacker@paths~position-elsewhere:~$ cd /tmp
hacker@paths~position-elsewhere:/tmp$ challenge/run
bash: challenge/run: No such file or directory
hacker@paths~position-elsewhere:/tmp$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{8De72TcqYUZOLVYFrO0fPx7tj5j.QX3QTN0wiNyAzNzEzW}
hacker@paths~position-elsewhere:/tmp$





```


### New Learnings
This was easier than the previous question as i had to be in the required directory (/tmp), before invoking the run command. 


  ## Position yet elsewhere

The Linux filesystem has tons of directories with tons of files. You can navigate around directories by using the cd (change directory) command and passing a path to it as an argument, as so:

 ```
  hacker@dojo:~$ cd /some/new/directory
hacker@dojo:/some/new/directory$  
```

This affects the "current working directory" of your process (in this case, the bash shell). Each process has a directory in which it's currently hanging out. The reasons for this will become clear later in the module.

As an aside, now you can see what the ~ was in the prompt! It shows the current path that your shell is located at.

This challenge will require you to execute the /challenge/run program from a specific path (which it will tell you). You'll need to cd to that directory before rerunning the challenge program. Good luck!

  ### Solve
  **Flag:** `pwn.college{kuXQPtq6YTs8fgZKAqPekI_AptO.QX4QTN0wiNyAzNzEzW}`  
```
Connected!
hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /usr/share/zoneinfo/posix/Asia directory.
Please use the cd utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:~$ /usr/share/zoneinfo/posix/Asia
bash: /usr/share/zoneinfo/posix/Asia: Is a directory
hacker@paths~position-yet-elsewhere:~$ cd /usr/share/zoneinfo/posix/Asia
hacker@paths~position-yet-elsewhere:/usr/share/zoneinfo/posix/Asia$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{kuXQPtq6YTs8fgZKAqPekI_AptO.QX4QTN0wiNyAzNzEzW}
hacker@paths~position-yet-elsewhere:/usr/share/zoneinfo/posix/Asia$




```


### New Learnings
This was easier than the previous question as i had to be in the required directory (/usr/share/zoneinfo/posix/Asia), before invoking the run command. I learned how to properly navigate through commands. Although mistakes are being made i am slowly learning the meaning of every command.
