# Comprehending Commands
  ## cat: not the pet, but the command! 

One of the most critical Linux commands is cat. cat is most often used for reading out files, like so:

```
hacker@dojo:~$ cat /challenge/DESCRIPTION.md
One of the most critical Linux commands is `cat`.
`cat` is most often used for reading out files, like so:

```

cat will concatenate (hence the name) multiple files if provided multiple arguments. For example:

```
hacker@dojo:~$ cat myfile
This is my file!
hacker@dojo:~$ cat yourfile
This is your file!
hacker@dojo:~$ cat myfile yourfile
This is my file!
This is your file!
hacker@dojo:~$ cat myfile yourfile myfile
This is my file!
This is your file!
This is my file!

```

Finally, if you give no arguments at all, cat will read from the terminal input and output it. We'll explore that in later challenges...

In this challenge, I will copy the flag to the flag file in your home directory (where your shell starts). Go read it with cat!

```
hacker@dojo:~$ cd /tmp
hacker@dojo:/tmp$ cd
hacker@dojo:~$
```


  ### Solve
  **Flag:** `pwn.college{QrGYY7FQ8-TV1ZynLymuWyXkEO4.QXxcTN0wiNyAzNzEzW}`  
```


Connected!
hacker@commands~cat-not-the-pet-but-the-command:~$ cat /flag
pwn.college{QrGYY7FQ8-TV1ZynLymuWyXkEO4.QXxcTN0wiNyAzNzEzW}
hacker@commands~cat-not-the-pet-but-the-command:~$


```


### New Learnings
I learned that the cat command printf out the content of a file, it doesnt do anything if there are other files in the directory.


  ## catting absolute paths 

In the last level, you did cat flag to read the flag out of your home directory! You can, of course, specify cat's arguments as absolute paths:

```
hacker@dojo:~$ cat /challenge/DESCRIPTION.md
In the last level, you did `cat flag` to read the flag out of your home directory!
You can, of course, specify `cat`'s arguments as absolute paths

```

In this directory, I will not copy it to your home directory, but I will make it readable. You can read it with cat at its absolute path: /flag.

FUN FACT: /flag is where the flag always lives in pwn.college, but unlike in this challenge, you typically can't access that file directly.



  ### Solve
  **Flag:** `pwn.college{8GxzVu8D2-dC4d0IU8mGCmOVrkb.QX5ETO0wiNyAzNzEzW}`  
```


Connected!
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{8GxzVu8D2-dC4d0IU8mGCmOVrkb.QX5ETO0wiNyAzNzEzW}
hacker@commands~catting-absolute-paths:~$



```


### New Learnings
In this i had to use absolute paths and use cat command directly without cding into the directory first.


  ## more catting practice

You can specify all sorts of paths as arguments to commands, and we'll practice some more with cat. In this level, I'll put the flag in some crazy directory, and I will not allow you to change directories with cd, so no cat flag for you. You must retrieve the flag by absolute path, wherever it is.



  ### Solve
  **Flag:** `pwn.college{09Z54MHInb3R19b-jV2hR4fp0QR.QXwITO0wiNyAzNzEzW}`  
```


Connected!
You cannot use the 'cd' command in this level, and must retrieve the flag by
absolute path. Plus, I hid the flag in a different directory! You can find it
in the file /usr/lib/bash/flag. Go cat it out *without* cding into that
directory!
hacker@commands~more-catting-practice:~$ cat /usr/lib/bash/flag
pwn.college{09Z54MHInb3R19b-jV2hR4fp0QR.QXwITO0wiNyAzNzEzW}
hacker@commands~more-catting-practice:~$



```


### New Learnings
In this i had to use absolute paths and use cat command directly without cding into the directory first. Since it gave me the address i just has to do cat /usr/lib/bash/flag to get the flag.


 ## grepping for a needle in a haystack

Sometimes, the files that you might cat out are too big. Luckily, we have the grep command to search for the contents we need! We'll learn it in this challenge.

There are many ways to grep, and we'll learn one way here:

```
hacker@dojo:~$ grep SEARCH_STRING /path/to/file
```
Invoked like this, grep will search the file for lines of text containing SEARCH_STRING and print them to the console.

In this challenge, I've put a hundred thousand lines of text into the /challenge/data.txt file. grep it for the flag!

HINT: The flag always starts with the text pwn.college.



  ### Solve
  **Flag:** `pwn.college{8l9-0hFDSAMXLAKwyvTFGNxqlM3.QX3EDO0wiNyAzNzEzW}`  
```


Connected!
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
pwn.college{8l9-0hFDSAMXLAKwyvTFGNxqlM3.QX3EDO0wiNyAzNzEzW}
hacker@commands~grepping-for-a-needle-in-a-haystack:~$



```


### New Learnings
I learned that grep is used when u need to print only certain necessary things. Here since i know i need to print the lines starting with pwn.college, i could find the flag by doing grep pwn.college /challenge/data.txt.


  ## comparing files

When looking for changes between similar files, eyeballing them might not be the most efficient approach! This is where the diff command becomes invaluable.

diff compares two files line by line and shows you exactly what's different between them. For example:

```
hacker@dojo:~$ cat file1
hello
world
hacker@dojo:~$ cat file2
hello
universe
hacker@dojo:~$ diff file1 file2
2c2
< world
---
> universe
```
The output tells us that line 2 changed (2c2), with world in the first file (<) being replaced by universe in the second file (>).

Sometimes, when new lines are added, you'll see something like:

```
hacker@dojo:~$ cat old
pwn
hacker@dojo:~$ cat new
pwn
college
hacker@dojo:~$ diff old new
1a2
> college
```
This tells us that after line 1 in the first file, the second file has an additional line (1a2 means "after line 1 of file1, add line 2 of file2").

Now for your challenge! There are two files in /challenge:

 - /challenge/decoys_only.txt contains 100 fake flags
 - /challenge/decoys_and_real.txt contains all 100 fake flags plus the one real flag
Use diff to find what's different between these files and get your flag!


  ### Solve
  **Flag:** `pwn.college{Uxc9lpbT9VwELnNPdGq4Yb8IIRc.01MwMDOxwiNyAzNzEzW}`  
```

Connected!
hacker@commands~comparing-files:~$ cd /challenge
hacker@commands~comparing-files:/challenge$ diff decoys_only.txt decoys_and_real.txt
5a6
> pwn.college{Uxc9lpbT9VwELnNPdGq4Yb8IIRc.01MwMDOxwiNyAzNzEzW}
hacker@commands~comparing-files:/challenge$


```


### New Learnings
I learned how to print the differences between 2 files, it also mentions which lines of which files are different making it easy to find in the file.


## listing files

So far, we've told you which files to interact with. But directories can have lots of files (and other directories) inside them, and we won't always be here to tell you their names. You'll need to learn to list their contents using the ls command!

ls will list files in all the directories provided to it as arguments, and in the current directory if no arguments are provided. Observe:

```
hacker@dojo:~$ ls /challenge
run
hacker@dojo:~$ ls
Desktop    Downloads  Pictures  Templates
Documents  Music      Public    Videos
hacker@dojo:~$ ls /home/hacker
Desktop    Downloads  Pictures  Templates
Documents  Music      Public    Videos
hacker@dojo:~$

```
In this challenge, we've named /challenge/run with some random name! List the files in /challenge to find it.



  ### Solve
  **Flag:** `pwn.college{kSTZ7hAJlaEL0upYwZWl5MxeJA3.QX4IDO0wiNyAzNzEzW}`  
```

Connected!
hacker@commands~listing-files:~$ ls /challenge
24271-renamed-run-8604  DESCRIPTION.md
hacker@commands~listing-files:~$ cat /challenge/24271-renamed-run-8604
#!/opt/pwn.college/bash

echo "Yahaha, you found me! Here is your flag:"
cat /flag
hacker@commands~listing-files:~$ ls /challenge/24271-renamed-run-8604
/challenge/24271-renamed-run-8604
hacker@commands~listing-files:~$ cd /challenge/24271-renamed-run-8604
bash: cd: /challenge/24271-renamed-run-8604: Not a directory
hacker@commands~listing-files:~$ ls /challenge/24271-renamed-run-8604
/challenge/24271-renamed-run-8604
hacker@commands~listing-files:~$ cat /challenge/24271-renamed-run-8604
#!/opt/pwn.college/bash

echo "Yahaha, you found me! Here is your flag:"
cat /flag
hacker@commands~listing-files:~$ /challenge/24271-renamed-run-8604
Yahaha, you found me! Here is your flag:
pwn.college{kSTZ7hAJlaEL0upYwZWl5MxeJA3.QX4IDO0wiNyAzNzEzW}
hacker@commands~listing-files:~$

```


### New Learnings
I learned that the ls command lists the files in a directory. I kept making the same mistake in this problem as i ran cat /challenge/24271-renamed-run-8604 istead of just running /challenge/24271-renamed-run-8604.


 ## touching files

Of course, you can also create files! There are several ways to do this, but we'll look at a simple command here. You can create a new, blank file by touching it with the touch command:
```
hacker@dojo:~$ cd /tmp
hacker@dojo:/tmp$ ls
hacker@dojo:/tmp$ touch pwnfile
hacker@dojo:/tmp$ ls
pwnfile
hacker@dojo:/tmp$
```
It's that simple! In this level, please create two files: /tmp/pwn and /tmp/college, and run /challenge/run to get your flag!



  ### Solve
  **Flag:** `pwn.college{QZ_r2l_jVqaEsMxAAjvPqWikH7p.QXwMDO0wiNyAzNzEzW}`  
```

Connected!
hacker@commands~touching-files:~$ cd /temp
bash: cd: /temp: No such file or directory
hacker@commands~touching-files:~$ cd /tmp
hacker@commands~touching-files:/tmp$ touch pwn
hacker@commands~touching-files:/tmp$ touch college
hacker@commands~touching-files:/tmp$ ls
bin  college  hsperfdata_root  pwn  tmp.TpSOPGOVKK
hacker@commands~touching-files:/tmp$ cd
hacker@commands~touching-files:~$ /challenge/run
Success! Here is your flag:
pwn.college{QZ_r2l_jVqaEsMxAAjvPqWikH7p.QXwMDO0wiNyAzNzEzW}
hacker@commands~touching-files:~$


```


### New Learnings
I learned how to create a file using the touch command.


## removing files

Files are all around you. Like candy wrappers, there'll eventually be too many of them. In this level, we'll learn to clean up!

In Linux, you remove files with the rm command, as so:
```
hacker@dojo:~$ touch PWN
hacker@dojo:~$ touch COLLEGE
hacker@dojo:~$ ls
COLLEGE     PWN
hacker@dojo:~$ rm PWN
hacker@dojo:~$ ls
COLLEGE
hacker@dojo:~$
```
Let's practice. This challenge will create a delete_me file in your home directory! Delete it, then run /challenge/check, which will make sure you've deleted it and then give you the flag!



  ### Solve
  **Flag:** `pwn.college{ohjv4k6NIzJd7pOfXA7U3EhXRUP.QX2kDM1wiNyAzNzEzW}`  
```

Connected!
hacker@commands~removing-files:~$ cd /
hacker@commands~removing-files:/$ ls
bin   challenge  etc   home  lib32  libx32  mnt  opt   root  sbin  sys  usr
boot  dev        flag  lib   lib64  media   nix  proc  run   srv   tmp  var
hacker@commands~removing-files:/$ cd home
hacker@commands~removing-files:/home$ ls
hacker
hacker@commands~removing-files:/home$ rm delete_me
rm: cannot remove 'delete_me': No such file or directory
hacker@commands~removing-files:/home$ cd hacker
hacker@commands~removing-files:~$ cd /home
hacker@commands~removing-files:/home$ rm hacker
rm: cannot remove 'hacker': Is a directory
hacker@commands~removing-files:/home$ cd
hacker@commands~removing-files:~$ ls
 delete_me  '~'
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{ohjv4k6NIzJd7pOfXA7U3EhXRUP.QX2kDM1wiNyAzNzEzW}
hacker@commands~removing-files:~$




```


### New Learnings
I learned how to delete/remove a file by using the rm command.


## moving files

You can also move files around with the mv command. The usage is simple:

```
hacker@dojo:~$ ls
my-file
hacker@dojo:~$ cat my-file
PWN!
hacker@dojo:~$ mv my-file your-file
hacker@dojo:~$ ls
your-file
hacker@dojo:~$ cat your-file
PWN!
hacker@dojo:~$

```
This challenge wants you to move the /flag file into /tmp/hack-the-planet (do it)! When you're done, run /challenge/check, which will check things out and give the flag to you.



  ### Solve
  **Flag:** `pwn.college{EV8qvq0pe8Q9YISlrDYJyEtdUIN.0VOxEzNxwiNyAzNzEzW}`  
```
Connected!
hacker@commands~moving-files:~$ mv /flag /tmp/hack-the-planet
Correct! Performing 'mv /flag /tmp/hack-the-planet'.
hacker@commands~moving-files:~$ /challenge/check
Congrats! You successfully moved the flag to /tmp/hack-the-planet! Here it is:
pwn.college{EV8qvq0pe8Q9YISlrDYJyEtdUIN.0VOxEzNxwiNyAzNzEzW}

hacker@commands~moving-files:~$



```


### New Learnings
I learned how to move a file from one directory to another, you do this by using the command mv (the file you want to move) (where you want to move the file).

## hidden files

Interestingly, ls doesn't list all the files by default. Linux has a convention where files that start with a . don't show up by default in ls and in a few other contexts. To view them with ls, you need to invoke ls with the -a flag, as so:

```
hacker@dojo:~$ touch pwn
hacker@dojo:~$ touch .college
hacker@dojo:~$ ls
pwn
hacker@dojo:~$ ls -a
.college	pwn
hacker@dojo:~$

```
Now, it's your turn! Go find the flag, hidden as a dot-prepended file in /.



  ### Solve
  **Flag:** `pwn.college{0UgUZWRP7kYKcK81fanxDN9jiCq.QXwUDO0wiNyAzNzEzW}`  
```
Connected!
hacker@commands~hidden-files:~$ ls
'~'
hacker@commands~hidden-files:~$ cd /
hacker@commands~hidden-files:/$ ls
bin   challenge  etc   lib    lib64   media  nix  proc  run   srv  tmp  var
boot  dev        home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~hidden-files:/$ ls -a
.                      bin        etc    lib64   nix   run   tmp
..                     boot       home   libx32  opt   sbin  usr
.dockerenv             challenge  lib    media   proc  srv   var
.flag-151121494126201  dev        lib32  mnt     root  sys
hacker@commands~hidden-files:/$ cd .flag-151121494126201
bash: cd: .flag-151121494126201: Not a directory
hacker@commands~hidden-files:/$ cd
hacker@commands~hidden-files:~$ cd /.flag-151121494126201
bash: cd: /.flag-151121494126201: Not a directory
hacker@commands~hidden-files:~$ cat /.flag-151121494126201
pwn.college{0UgUZWRP7kYKcK81fanxDN9jiCq.QXwUDO0wiNyAzNzEzW}
hacker@commands~hidden-files:~$




```


### New Learnings
I learned that to find hidden files ( files which have . at the starting of them), i need to use ls -a instead of just normal ls to list out those files.


## An Epic Filesystem Quest

With your knowledge of cd, ls, and cat, we're ready to play a little game!

We'll start it out in /. Normally:

```
hacker@dojo:~$ cd /
hacker@dojo:/$ ls
bin   challenge  etc   home  lib32  libx32  mnt  proc  run   srv  tmp  var
boot  dev        flag  lib   lib64  media   opt  root  sbin  sys  usr

```
That's a lot of contents! One day, you will be quite familiar with them, but already, you might recognize the flag file and the challenge directory.

In this challenge, I have hidden the flag! Here, you will use ls and cat to follow my breadcrumbs and find it! Here's how it'll work:

0. Your first clue is in /. Head on over there.
1. Look around with ls. There'll be a file named HINT or CLUE or something along those lines!
2. cat that file to read the clue!
3. Depending on what the clue says, head on over to the next directory (or don't!).
4. Follow the clues to the flag!
Good luck!


  ### Solve
  **Flag:** `pwn.college{M1oB6IO9YaNtozrt2z_hsgdvafr.QX5IDO0wiNyAzNzEzW}`  

```
Connected!
hacker@commands~an-epic-filesystem-quest:~$ cd /
hacker@commands~an-epic-filesystem-quest:/$ ls
HINT  challenge  flag  lib32   media  opt   run   sys  var
bin   dev        home  lib64   mnt    proc  sbin  tmp
boot  etc        lib   libx32  nix    root  srv   usr
hacker@commands~an-epic-filesystem-quest:/$ cat HINT
Lucky listing!
The next clue is in: /opt/linux/linux-5.4/arch/sparc/boot

The next clue is *hidden* --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/$ cd
hacker@commands~an-epic-filesystem-quest:~$ cd /opt/linux/linux-5.4/arch/sparc/boot
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/sparc/boot$ ls
Makefile  install.sh  piggyback.c
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/sparc/boot$ ls -a
.  ..  .NUGGET  .gitignore  Makefile  install.sh  piggyback.c
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/sparc/boot$ cat .NUGGET
Yahaha, you found me!
The next clue is in: /opt/busybox/busybox-1.33.2/testsuite/cp

Watch out! The next clue is *trapped*. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/sparc/boot$ cd
hacker@commands~an-epic-filesystem-quest:~$ ls /opt/busybox/busybox-1.33.2/testsuite/cp
INSIGHT-TRAPPED                 cp-dir-create-dir
cp-RHL-does_not_preserve-links  cp-dir-existing-dir
cp-a-files-to-dir               cp-does-not-copy-unreadable-file
cp-a-preserves-links            cp-files-to-dir
cp-copies-empty-file            cp-follows-links
cp-copies-large-file            cp-parents
cp-copies-small-file            cp-preserves-hard-links
cp-d-files-to-dir               cp-preserves-links
cp-dev-file                     cp-preserves-source-file
hacker@commands~an-epic-filesystem-quest:~$ cat /opt/busybox/busybox-1.33.2/testsuite/cp/INSIGHT-TRAPPED
Lucky listing!
The next clue is in: /usr/local/lib/python3.8/dist-packages/pysmt/test/smtlib

The next clue is *delayed* --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:~$ cd /usr/local/lib/python3.8/dist-packages/pysmt/test/smtlib
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/pysmt/test/smtlib$ ls
README                        test_parser_lra.py
_init_.py                   test_parser_qf_arrays.py
_pycache_                   test_parser_qf_lia.py
parser_utils.py               test_parser_qf_lira.py
test_annotations.py           test_parser_qf_lra.py
test_fuzzed.py                test_parser_qf_nia.py
test_generic_wrapper.py       test_parser_qf_nra.py
test_griggio.py               test_parser_qf_uf.py
test_model_validation.py      test_parser_qf_ufbv.py
test_parser_examples.py       test_parser_type_error.py
test_parser_extensibility.py  test_smtlibscript.py
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/pysmt/test/smtlib$ cat README
Great sleuthing!
The next clue is in: /usr/local/lib/python3.8/dist-packages/numpy/tests/_pycache_
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/pysmt/test/smtlib$ cd
hacker@commands~an-epic-filesystem-quest:~$ /usr/local/lib/python3.8/dist-packages/numpy/tests/_pycache_
bash: /usr/local/lib/python3.8/dist-packages/numpy/tests/_pycache_: Is a directory
hacker@commands~an-epic-filesystem-quest:~$ cat /usr/local/lib/python3.8/dist-packages/numpy/tests/_pycache_
cat: /usr/local/lib/python3.8/dist-packages/numpy/tests/_pycache_: Is a directory
hacker@commands~an-epic-filesystem-quest:~$ ls /usr/local/lib/python3.8/dist-packages/numpy/tests/_pycache_
CLUE                             test_numpy_version.cpython-38.pyc
_init_.cpython-38.pyc          test_public_api.cpython-38.pyc
test_all_.cpython-38.pyc       test_reloading.cpython-38.pyc
test_ctypeslib.cpython-38.pyc    test_scripts.cpython-38.pyc
test_lazyloading.cpython-38.pyc  test_warnings.cpython-38.pyc
test_matlib.cpython-38.pyc
hacker@commands~an-epic-filesystem-quest:~$ cat /usr/local/lib/python3.8/dist-packages/numpy/tests/_pycache_/CLUE
Congratulations, you found the clue!
The next clue is in: /usr/share/emacs/26.3/etc/images/icons/hicolor/24x24

Watch out! The next clue is *trapped*. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:~$ ls /usr/share/emacs/26.3/etc/images/icons/hicolor/24x24
CUE-TRAPPED  apps
hacker@commands~an-epic-filesystem-quest:~$ cat /usr/share/emacs/26.3/etc/images/icons/hicolor/24x24/CUE-TRAPPED
Yahaha, you found me!
The next clue is in: /opt/linux/linux-5.4/net/netrom

The next clue is *hidden* --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:~$ ls -a /opt/linux/linux-5.4/net/netrom
.      Makefile     nr_in.c        nr_route.c  sysctl_net_netrom.c
..     af_netrom.c  nr_loopback.c  nr_subr.c
.GIST  nr_dev.c     nr_out.c       nr_timer.c
hacker@commands~an-epic-filesystem-quest:~$ cat /opt/linux/linux-5.4/net/netrom/GIST
cat: /opt/linux/linux-5.4/net/netrom/GIST: No such file or directory
hacker@commands~an-epic-filesystem-quest:~$ cat /opt/linux/linux-5.4/net/netrom/.GIST
Lucky listing!
The next clue is in: /opt/linux/linux-5.4/Documentation/PCI/endpoint
hacker@commands~an-epic-filesystem-quest:~$ cd /opt/linux/linux-5.4/Documentation/PCI/endpoint
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/Documentation/PCI/endpoint$ ls
WHISPER   index.rst             pci-endpoint.rst       pci-test-howto.rst
function  pci-endpoint-cfs.rst  pci-test-function.rst
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/Documentation/PCI/endpoint$ cat WHISPER
Yahaha, you found me!
The next clue is in: /opt/linux/linux-5.4/Documentation/admin-guide/gpio

The next clue is *delayed* --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/Documentation/PCI/endpoint$ cd /opt/linux/linux-5.4/Documentation/admin-guide/gpio
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/Documentation/admin-guide/gpio$ ls
EVIDENCE  index.rst  sysfs.rst
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/Documentation/admin-guide/gpio$ cat /opt/linux/linux-5.4/Documentation/admin-guide/gpio/^C
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/Documentation/admin-guide/gpio$ cat EVIDENCE
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{M1oB6IO9YaNtozrt2z_hsgdvafr.QX5IDO0wiNyAzNzEzW}
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/Documentation/admin-guide/gpio$





```


### New Learnings
This was my favourite problem so far as it had me practice all the commands i learned so far. It kept giging me addresses which i kept cding to and reading the necessary file using cat command.
