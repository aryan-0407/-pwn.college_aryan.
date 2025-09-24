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



  ## Implicit relative paths, from /

Now you're familiar with the concept of referring to absolute paths and changing directories. If you put in absolute paths everywhere, then it really doesn't matter what directory you are in, as you likely found out in the previous three challenges.

However, the current working directory does matter for relative paths.

1) A relative path is any path that does not start at root  (i.e., it does not start with /).
2) A relative path is interpreted relative to your current working directory (cwd).
3) Your cwd is the directory that your prompt is currently located at.

This means how you specify a particular file, depends on where the terminal prompt is located.

Imagine we want to access some file located at /tmp/a/b/my_file.

1) If my cwd is /, then a relative path to the file is tmp/a/b/my_file.
2) If my cwd is /tmp, then a relative path to the file is a/b/my_file.
3) If my cwd is /tmp/a/b/c, then a relative path to the file is ../my_file. The .. refers to the parent directory.


Let's try it here! You'll need to run /challenge/run using a relative path while having a current working directory of /. For this level, I'll give you a hint. Your relative path starts with the letter c 😊

  ### Solve
  **Flag:** `pwn.college{8DAL_WzJHqtdQruImDcpG9KbMDJ.QX5QTN0wiNyAzNzEzW}`  
```
Connected!
hacker@paths~implicit-relative-paths-from-:~$ /challenge/run
Incorrect...
You are not currently in the / directory.
Please use the cd utility to change directory appropriately.
hacker@paths~implicit-relative-paths-from-:~$ cd /challenge/run
bash: cd: /challenge/run: Not a directory
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ ls
bin   challenge  etc   home  lib32  libx32  mnt  opt   root  sbin  sys  usr
boot  dev        flag  lib   lib64  media   nix  proc  run   srv   tmp  var
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{8DAL_WzJHqtdQruImDcpG9KbMDJ.QX5QTN0wiNyAzNzEzW}
hacker@paths~implicit-relative-paths-from-:/$



```


### New Learnings
Here i first had to go to the / directory. From there i had the run the challenge/run command. This gave me the flag. 


  ## Explicit relative paths, from /

Previously, your relative path was "naked": it directly specified the directory to descend into from the current directory. In this level, we're going to explore more explicit relative paths.

In most operating systems, including Linux, every directory has two implicit entries that you can reference in paths: . and ... The first, ., refers right to the same directory, so the following absolute paths are all identical to each other:

 - /challenge
 - /challenge/.
 - /challenge/./././././././././
 - /./././challenge/././

The following relative paths are also all identical to each other:

 - challenge
 - ./challenge
 - ./././challenge
 - challenge/.

Of course, if your current working directory is /, the above relative paths are equivalent to the above absolute paths.

This challenge will get you using . in your relative paths. Get ready!

  ### Solve
  **Flag:** `pwn.college{wh5hciYE3IKpuUk5xI3b2z8Y7ww.QXwUTN0wiNyAzNzEzW}`  
```
Connected!
hacker@paths~explicit-relative-paths-from-:~$ cd /
hacker@paths~explicit-relative-paths-from-:/$ ls
bin   challenge  etc   home  lib32  libx32  mnt  opt   root  sbin  sys  usr
boot  dev        flag  lib   lib64  media   nix  proc  run   srv   tmp  var
hacker@paths~explicit-relative-paths-from-:/$ cd challenge
hacker@paths~explicit-relative-paths-from-:/challenge$ ls
DESCRIPTION.md  run
hacker@paths~explicit-relative-paths-from-:/challenge$ cd run
bash: cd: run: Not a directory
hacker@paths~explicit-relative-paths-from-:/challenge$ cd
hacker@paths~explicit-relative-paths-from-:~$ /challenge/run
Incorrect...
You are not currently in the / directory.
Please use the cd utility to change directory appropriately.
hacker@paths~explicit-relative-paths-from-:~$ /challenge/run/../
bash: /challenge/run/../: Not a directory
hacker@paths~explicit-relative-paths-from-:~$ /challenge/.
bash: /challenge/.: Is a directory
hacker@paths~explicit-relative-paths-from-:~$ cd /challenge/.
hacker@paths~explicit-relative-paths-from-:/challenge$ cd /run/.
hacker@paths~explicit-relative-paths-from-:/run$ ls
apache2         firefox-restart-required  mysqld           sudo
challenge       lock                      screen           systemd
current-system  log                       sendsigs.omit.d  user
dojo            mount                     shm              utmp
hacker@paths~explicit-relative-paths-from-:/run$ cd
hacker@paths~explicit-relative-paths-from-:~$ /challenge/run
Incorrect...
You are not currently in the / directory.
Please use the cd utility to change directory appropriately.
hacker@paths~explicit-relative-paths-from-:~$ cd /
hacker@paths~explicit-relative-paths-from-:/$ challenge/run
Incorrect...
This challenge must be called with a relative path that explicitly starts with a .!
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{wh5hciYE3IKpuUk5xI3b2z8Y7ww.QXwUTN0wiNyAzNzEzW}
hacker@paths~explicit-relative-paths-from-:/$




```


### New Learnings
Here i first had to go to the / directory aswell. From there ran the challenge/run command. This gave me an error message saying my challenge must be called with a relative path that starts with '.', so then i did ./challenge/run which worked.


  ## Implicit relative path

In this level, we'll practice referring to paths using . a bit more. This challenge will need you to run it from the /challenge directory. Here, things get slightly tricky.

Linux explicitly avoids automatically looking in the current directory when you provide a "naked" path. Consider the following:

```
hacker@dojo:~$ cd /challenge
hacker@dojo:/challenge$ run
```

This will not invoke /challenge/run. This is actually a safety measure: if Linux searched the current directory for programs every time you entered a naked path, you could accidentally execute programs in your current directory that happened to have the same names as core system utilities! As a result, the above commands will yield the following error:

```
bash: run: command not found
```

We'll explore the mechanisms behind this concept later, but in this challenge, we'll learn how to explicitly use relative paths to launch run in this scenario. The way to do this is to tell Linux that you explicitly want to execute a program in the current directory, using . like in the previous levels. Give it a try now!

  ### Solve
  **Flag:** `pwn.college{QYP1mgrfOn4W5ekLSfKZEjjaDGw.QXxUTN0wiNyAzNzEzW}`  
```

Connected!
hacker@paths~implicit-relative-path:~$ cd challenge
bash: cd: challenge: No such file or directory
hacker@paths~implicit-relative-path:~$ cd /challenge
hacker@paths~implicit-relative-path:/challenge$ .run
bash: .run: command not found
hacker@paths~implicit-relative-path:/challenge$ run.
bash: run.: command not found
hacker@paths~implicit-relative-path:/challenge$ run/.
bash: run/.: Not a directory
hacker@paths~implicit-relative-path:/challenge$ /.run
bash: /.run: No such file or directory
hacker@paths~implicit-relative-path:/challenge$ cd /.run
bash: cd: /.run: No such file or directory
hacker@paths~implicit-relative-path:/challenge$ cd run/.
bash: cd: run/.: Not a directory
hacker@paths~implicit-relative-path:/challenge$ cd
hacker@paths~implicit-relative-path:~$ cd /
hacker@paths~implicit-relative-path:/$ challenge./run
bash: challenge./run: No such file or directory
hacker@paths~implicit-relative-path:/$ ./challenge/run
Incorrect...
You are not currently in the /challenge directory.
Please use the cd utility to change directory appropriately.
hacker@paths~implicit-relative-path:/$ cd challenge
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{QYP1mgrfOn4W5ekLSfKZEjjaDGw.QXxUTN0wiNyAzNzEzW}
hacker@paths~implicit-relative-path:/challenge$




```


### New Learnings
Here i first had to go to the / directory aswell. From there ran the challenge/run command. This gave me an error message saying my challenge must be called with a relative path that starts with '.', so then i did ./challenge/run which worked.


  ## home sweet home 

Every user has a home directory, typically under /home in the filesystem. In the dojo, you are the hacker user, and your home directory is /home/hacker. The home directory is typically where users store most of their personal files. As you make your way through pwn.college, this is where you'll store most of your solutions.

Typically, your shell session will start with your home directory as your current working directory. Consider the initial prompt:

```
hacker@dojo:~$
```

The ~ in this prompt is the current working directory, with ~ being shorthand for /home/hacker. Bash provides and uses this shorthand because, again, most of your time will be spent in your home directory. Thus, whenever bash sees ~ provided as the start of an argument in a way consistent with a path, it will expand it to your home directory. Consider:

```
hacker@dojo:~$ echo LOOK: ~
LOOK: /home/hacker
hacker@dojo:~$ cd /
hacker@dojo:/$ cd ~
hacker@dojo:~$ cd ~/asdf
hacker@dojo:~/asdf$ cd ~/asdf
hacker@dojo:~/asdf$ cd ~
hacker@dojo:~$ cd /home/hacker/asdf
hacker@dojo:~/asdf$
```

Note that the expansion of ~ is an absolute path, and only the leading ~ is expanded. This means, for example, that ~/~ will be expanded to /home/hacker/~ rather than /home/hacker/home/hacker.

Fun fact: cd will use your home directory as the default destination:

```
hacker@dojo:~$ cd /tmp
hacker@dojo:/tmp$ cd
hacker@dojo:~$
```

Now it's your turn to play! In this challenge, /challenge/run will write a copy of the flag to any file you specify as an argument on the commandline, with these constraints:

Your argument must be an absolute path.
The path must be inside your home directory.
Before expansion, your argument must be three characters or less.
Again, you must specify your path as an argument to /challenge/run as so:

```
hacker@dojo:~$ /challenge/run YOUR_PATH_HERE
```

  ### Solve
  **Flag:** `pwn.college{IvTZhRlaXdSZrC_G7WVEL2eVi0D.QXzMDO0wiNyAzNzEzW}`  
```


Connected!
hacker@paths~home-sweet-home:~$ ls
hacker@paths~home-sweet-home:~$ /challenge/run
You must provide an argument to /challenge/run when you invoke it!
hacker@paths~home-sweet-home:~$ /challenge/run /home
The argument you provided must not have been longer than 3 characters (it's
currently 5 characters long)!
hacker@paths~home-sweet-home:$ /challenge/run /
The argument you provided is not under your home directory!
hacker@paths~home-sweet-home:~$ /challenge/run ~/
Writing the file to /home/hacker/!
/challenge/run: line 29: /home/hacker/: Is a directory
... and reading it back to you:
cat: /home/hacker/: Is a directory
hacker@paths~home-sweet-home:$ /challenge/run ~/
Writing the file to /home/hacker/~!
... and reading it back to you:
pwn.college{IvTZhRlaXdSZrC_G7WVEL2eVi0D.QXzMDO0wiNyAzNzEzW}
hacker@paths~home-sweet-home:~$




```


### New Learnings
In this problem i had to ensure i dont make an arguement over 3 characters long, so i looked at one of the examples and did ~/, this had only 2 characters. This gave me the flag for the problem. I also lerned what the look command does through the examples.

