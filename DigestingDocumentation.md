 # Digesting Documentation
  ## Learning from Documentation

The typical need you'll have for documentation is just to figure out how to use all these dang programs, and a specific case of that is figuring out what arguments to specify on the command line. This module will mostly dig into that concept, as a proxy for figuring out how to use the programs in general. Through the rest of the module, you'll go through various ways of asking the environment for help for the programs, but first, we'll dig into the concept of reading documentation.

The correct usage of programs depends, in a large part, on the proper specification of arguments to them. Recall the -a of ls -a in the hidden files challenge of the Basic Commands module: that -a was an argument that told ls to list out hidden files as well as non-hidden files. Because we wanted to list out hidden files, invoking ls with the -a argument was the correct way to use it in our scenario.

The program for this challenge is /challenge/challenge, and you'll need to invoke it properly in order for it to give you the flag. Let's pretend that this is its documentation:

Welcome to the documentation for /challenge/challenge! To properly run this program, you will need to pass it the argument of --giveflag. Good luck!

Given that knowledge, go get the flag!

  ### Solve
  **Flag:** `pwn.college{gJnd3IaNp5Z7k4G8jMBq6eXVcWh.QX0ITO0wiNyAzNzEzW}`  

```
Connected!
hacker@man~learning-from-documentation:~$ --giveflag /challenge/challenge
bash: --giveflag: command not found
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{gJnd3IaNp5Z7k4G8jMBq6eXVcWh.QX0ITO0wiNyAzNzEzW}
hacker@man~learning-from-documentation:~$





```


### New Learnings
I learned about commands and arguements. I used the command /challenge/challenge with the arguement --giveflag whch gave me the flag.

  ## Learning Complex Usage

While using most commands is straightforward, the usage of some commands can get quite complex. For example, the arguments to commands like sed and awk, which we're definitely not getting into right now, are entire programs in an esoteric programming language! Somewhere on the spectrum between cd and awk are commands that take arguments to their arguments...

This sounds crazy, but you've already encountered this with the find level in Basic Commands. find has a -name argument, and the -name argument itself takes an argument specifying the name to search for. Many other commands are analogous.

Here is this level's documentation for /challenge/challenge:

Welcome to the documentation for /challenge/challenge! This program allows you to print arbitrary files to the terminal, when given the --printfile argument. The argument to the --printfile argument is the path of the flag to read. For example, /challenge/challenge --printfile /challenge/DESCRIPTION.md will print out the description of the level!

Given that documentation, go get the flag!

Given that knowledge, go get the flag!

  ### Solve
  **Flag:** `pwn.college{wQwSPz0WPt2x7XM3xxTs2OExyze.QX1ITO0wiNyAzNzEzW}`  

```
Connected!
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /challenge/challenge
Correct argument! Here is the /challenge/challenge file:
#!/opt/pwn.college/bash

if [ "$#" -eq 0 ]
then
        fold -s <<< "Incorrect usage! You must pass an argument to me (read the challenge description for details)."
        exit 1
fi

if [ "$1" != "--printfile" ]
then
        fold -s <<< "Incorrect usage! You passed the wrong argument (read the challenge description for details)."
        exit 2
fi

if [ "$#" -eq 1 ]
then
        fold -s <<< "You must pass a file for --printfile to read!"
        exit 3
fi

echo "Correct argument! Here is the $2 file:"
cat "$2"
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /flag
Correct argument! Here is the /flag file:
pwn.college{wQwSPz0WPt2x7XM3xxTs2OExyze.QX1ITO0wiNyAzNzEzW}
hacker@man~learning-complex-usage:~$




```


### New Learnings
I learned more about commands and arguements. I learned that agruements of commands have arguements themselves. Here i had to give the arguement /flag another arguement --printfile whose function was to print whatever was in the file.


 # Digesting Documentation
  ## Reading Manuals

This level introduces the man command. man is short for manual, and will display (if available) the manual of the command you pass as an argument. For example, let's say we wanted to learn about the yes command (yes, this is a real command):

```
hacker@dojo:~$ man yes
```

You can scroll around the manpage with your arrow keys and PgUp/PgDn. When you're done reading the manpage, you can hit q to quit.

Manpages are stored in a centralized database. If you're curious, this database lives in the /usr/share/man directory, but you never need to interact with it directly: you just query it using the man command. The arguments to the man command aren't file paths, but just the names of the entries themselves (e.g., you run man yes to look up the yes manpage, rather than man /usr/bin/yes, which would be the actual path to the yes program but would result in man displaying garbage).

The challenge in this level has a secret option that, when you use it, will cause the challenge to print the flag. You must learn this option through the man page for challenge!

  ### Solve
  **Flag:** `pwn.college{YnUD8I4Q2j5f3jr9dRVJM9qSLHs.QX0EDO0wiNyAzNzEzW}`  

```
Connected!
hacker@man~reading-manuals:~$ man challenge
hacker@man~reading-manuals:~$
hacker@man~reading-manuals:~$ man challenge
hacker@man~reading-manuals:~$ --njfjrd 842
bash: --njfjrd: command not found
hacker@man~reading-manuals:~$ /challenge/challenge --njfjrd 842
Correct usage! Your flag: pwn.college{YnUD8I4Q2j5f3jr9dRVJM9qSLHs.QX0EDO0wiNyAzNzEzW}
hacker@man~reading-manuals:~$




```


### New Learnings
I learned how to open manual pages. Here i opened the manual using man challenge then used the secret command in the page which have me the flag.


  ## Searching Manuals

You can scroll man pages with the arrow keys (and PgUp/PgDn) and search with /. After searching, you can hit n to go to the next result and N to go to the previous result. Instead of /, you can use ? to search backwards!

Find the option that will give you the flag by reading the challenge man page.

  ### Solve
  **Flag:** `pwn.college{sZMXfPTk_l_JD4aw_6t2YvaaDPp.QX1EDO0wiNyAzNzEzW}`  

```
Connected!
hacker@man~searching-manuals:~$ man challenge
hacker@man~searching-manuals:~$ /challenge/challenge --revtdt
Initializing...
Correct usage! Your flag: pwn.college{sZMXfPTk_l_JD4aw_6t2YvaaDPp.QX1EDO0wiNyAzNzEzW}
hacker@man~searching-manuals:~$




```


### New Learnings
I learned how to navigate through manual pages by using the arrow keys or even my mouses scroll wheel. Using this i found the command which gives me the flag.

## Searching For Manuals

This level is tricky: it hides the manpage for the challenge by randomizing its name. Luckily, all of the manpages are gathered in a searchable database, so you'll be able to search the man page database to find the hidden challenge man page! To figure out how to search for the right manpage, read the man page manpage by doing: man man!

HINT 1: man man teaches you advanced usage of the man command itself, and you must use this knowledge to figure out how to search for the hidden manpage that will tell you how to use /challenge/challenge

HINT 2: though the manpage is randomly named, you still actually use /challenge/challenge to get the flag!

  ### Solve
  **Flag:** `pwn.college{ctQaCFAWr75EiCAjcEgrP8M5KDK.QX2EDO0wiNyAzNzEzW}`  

```
Connected!
hacker@man~searching-for-manuals:~$ man man
hacker@man~searching-for-manuals:~$ man -k
apropos what?
hacker@man~searching-for-manuals:~$ man man
hacker@man~searching-for-manuals:~$ man -k
apropos what?
hacker@man~searching-for-manuals:~$ man -K
What manual page do you want?
For example, try 'man man'.
hacker@man~searching-for-manuals:~$ man man
hacker@man~searching-for-manuals:~$
hacker@man~searching-for-manuals:~$ man -k flag
ctarijcgrw (1)       - print the flag!
dpkg-buildflags (1)  - returns build flags to use during package build
Dpkg::BuildFlags (3perl) - query build flags
fegetexceptflag (3)  - floating-point rounding and exception handling
fesetexceptflag (3)  - floating-point rounding and exception handling
i386 (8)             - change reported architecture in new program enviro...
ioctl_iflags (2)     - ioctl() operations for inode flags
linux32 (1)          - change reported architecture in new program enviro...
linux64 (1)          - change reported architecture in new program enviro...
pcap-config (1)      - write libpcap compiler and linker flags to standar...
security_compute_av_flags (3) - query the SELinux policy database in the ...
security_compute_av_flags_raw (3) - query the SELinux policy database in ...
set_matchpathcon_flags (3) - set flags controlling the operation of match...
set_matchpathcon_invalidcon (3) - set flags controlling the operation of ...
set_matchpathcon_printf (3) - set flags controlling the operation of matc...
setarch (1)          - change reported architecture in new program enviro...
setarch (8)          - change reported architecture in new program enviro...
x86_64 (8)           - change reported architecture in new program enviro...
hacker@man~searching-for-manuals:~$ man ctarijcgrw
hacker@man~searching-for-manuals:~$ man --ctarij 752
man: unrecognized option '--ctarij'
Try 'man --help' or 'man --usage' for more information.
hacker@man~searching-for-manuals:~$ man ctarijcgrw
hacker@man~searching-for-manuals:~$ man --ctarij 758
man: unrecognized option '--ctarij'
Try 'man --help' or 'man --usage' for more information.
hacker@man~searching-for-manuals:~$ /challenge/challenge --ctarij 758
Correct usage! Your flag: pwn.college{ctQaCFAWr75EiCAjcEgrP8M5KDK.QX2EDO0wiNyAzNzEzW}
hacker@man~searching-for-manuals:~$





```


### New Learnings
This level was the hardest one i faced so far. When i opened the manual i didntfind anything thatd be helpful to me. Then i looked it up online where i found the command man -k flag, this command showed me which command i have to use to find the flag, so i did.

## Helpful Programs

Some programs don't have a man page, but might tell you how to run them if invoked with a special argument. Usually, this argument is --help, but it can often be -h or, in rare cases, -?, help, or other esoteric values like /? (though that latter is more frequently encountered on Windows).

In this level, you will practice reading a program's documentation with --help. Try it out!


  ### Solve
  **Flag:** `pwn.college{EriN17xU2iGvWWrmY9tQa5ab3xw.QX3IDO0wiNyAzNzEzW}`  

```
Connected!
hacker@man~helpful-programs:~$ --help
bash: --help: command not found
hacker@man~helpful-programs:~$ cd /
hacker@man~helpful-programs:/$ ls
bin   challenge  etc   home  lib32  libx32  mnt  opt   root  sbin  sys  usr
boot  dev        flag  lib   lib64  media   nix  proc  run   srv   tmp  var
hacker@man~helpful-programs:/$ cd
hacker@man~helpful-programs:~$ /challenge/challenge --help
usage: a challenge to make you ask for help [-h] [--fortune] [-v]
                                            [-g GIVE_THE_FLAG] [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to
                        give you the flag
hacker@man~helpful-programs:~$ /challenge/challenge -p
The secret value is: 172
hacker@man~helpful-programs:~$ /challenge/challenge --give-the-flag 172
Correct usage! Your flag: pwn.college{EriN17xU2iGvWWrmY9tQa5ab3xw.QX3IDO0wiNyAzNzEzW}
hacker@man~helpful-programs:~$





```


### New Learnings
Once i understood how to do the 5th problem this seemed pretty easy. All i had to do was use the help command in the /challenge/challenge file. It then told me to use the cgiven commands with its secter number which gives me the flag.


## Help for Builtins

Some commands, rather than being programs with man pages and help options, are built into the shell itself. These are called builtins. Builtins are invoked just like commands, but the shell handles them internally instead of launching other programs. You can get a list of shell builtins by running the builtin help, as so:

```
hacker@dojo:~$ help
```

You can get help on a specific one by passing it to the help builtin. Let's look at a builtin that we've already used earlier, cd!

Some good information! In this challenge, we'll practice using help to look up help for builtins. This challenge's challenge command is a shell builtin, rather than a program. Like before, you need to lookup its help to figure out the secret value to pass to it!


  ### Solve
  **Flag:** `pwn.college{Ar5ZPdhxEXmOMPXXN-vyOo8q2NI.QX0ETO0wiNyAzNzEzW}`  

```
Connected!
hacker@man~help-for-builtins:~$ help challenge
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!

    Options:
      --fortune         display a fortune
      --version         display the version
      --secret VALUE    prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "Ar5ZPdhx".
hacker@man~help-for-builtins:~$ /challenge/challenge --secret Ar5ZPdhx
bash: /challenge/challenge: No such file or directory
hacker@man~help-for-builtins:~$ --secret Ar5ZPdhx
bash: --secret: command not found
hacker@man~help-for-builtins:~$ challenge --secret Ar5ZPdhx
Correct! Here is your flag!
pwn.college{Ar5ZPdhxEXmOMPXXN-vyOo8q2NI.QX0ETO0wiNyAzNzEzW}

hacker@man~help-for-builtins:~$ pwn.college{Ar5ZPdhxEXmOMPXXN-vyOo8q2NI.QX0ETO0wiNyAzNzEzW}




```


### New Learnings
Here i had to do help challenge which have a bunch of text explaining what to do. Based on what it gave i did challenge --secret Ar5ZPdhx which gave me the flag.
