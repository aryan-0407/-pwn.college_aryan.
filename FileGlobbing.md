 # File Globbing
  ## Matching with *

The first glob we'll learn is *. When it encounters a * character in any argument, the shell will treat it as a "wildcard" and try to replace that argument with any files that match the pattern. It's easier to show you than explain:

```
hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_c
hacker@dojo:~$ ls
file_a	file_b	file_c
hacker@dojo:~$ echo Look: file_*
Look: file_a file_b file_c

```

Of course, though in this case, the glob resulted in multiple arguments, it can just as simply match only one. For example:
```
hacker@dojo:~$ touch file_a
hacker@dojo:~$ ls
file_a
hacker@dojo:~$ echo Look: file_*
Look: file_a
```
When zero files are matched, by default, the shell leaves the glob unchanged:
```
hacker@dojo:~$ touch file_a
hacker@dojo:~$ ls
file_a
hacker@dojo:~$ echo Look: nope_*
Look: nope_*
```
The * matches any part of the filename except for / or a leading . character. For example:
```
hacker@dojo:~$ echo ONE: /ho*/*ck*
ONE: /home/hacker
hacker@dojo:~$ echo TWO: /*/hacker
TWO: /home/hacker
hacker@dojo:~$ echo THREE: ../*
THREE: ../hacker
```

Now, practice this yourself! Starting from your home directory, change your directory to /challenge, but use globbing to keep the argument you pass to cd to at most four characters! Once you're there, run /challenge/run for the flag!


  ### Solve
  **Flag:** `pwn.college{sbjwZ6beUKybcx_SJYYzGkvTf6n.QXxIDO0wiNyAzNzEzW}`  

```
Connected!
This challenge resets your working directory to /home/hacker unless you change
directory properly...
This challenge resets your working directory to /home/hacker unless you change
directory properly...
hacker@globbing~matching-with-:~$ /c*
This challenge resets your working directory to /home/hacker unless you change
directory properly...
bash: /challenge: Is a directory
This challenge resets your working directory to /home/hacker unless you change
directory properly...
This challenge resets your working directory to /home/hacker unless you change
directory properly...
hacker@globbing~matching-with-:~$ /c*/
This challenge resets your working directory to /home/hacker unless you change
directory properly...
bash: /challenge/: Is a directory
This challenge resets your working directory to /home/hacker unless you change
directory properly...
This challenge resets your working directory to /home/hacker unless you change
directory properly...
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{sbjwZ6beUKybcx_SJYYzGkvTf6n.QXxIDO0wiNyAzNzEzW}
hacker@globbing~matching-with-:/challenge$





```


### New Learnings
It took me a few tries but i understood how to use the * glob. * means the shell will treat it as a wildcard(randomized character).


## Matching with ?
Next, let's learn about ?. When it encounters a ? character in any argument, the shell will treat it as a single-character wildcard. This works like *, but only matches one character. For example:
```
hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_cc
hacker@dojo:~$ ls
file_a	file_b	file_cc
hacker@dojo:~$ echo Look: file_?
Look: file_a file_b
hacker@dojo:~$ echo Look: file_??
Look: file_cc
```
Now, practice this yourself! Starting from your home directory, change your directory to /challenge, but use the ? character instead of c and l in the argument to cd! Once you're there, run /challenge/run for the flag!

  ### Solve
  **Flag:** `pwn.college{EHg162o2mHxtCm4umNqHcbrTSEn.QXyIDO0wiNyAzNzEzW}`  

```
Connected!
This challenge resets your working directory to /home/hacker unless you change
directory properly...
This challenge resets your working directory to /home/hacker unless you change
directory properly...
hacker@globbing~matching-with-:~$ /?ha??enge
This challenge resets your working directory to /home/hacker unless you change
directory properly...
bash: /challenge: Is a directory
This challenge resets your working directory to /home/hacker unless you change
directory properly...
This challenge resets your working directory to /home/hacker unless you change
directory properly...
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{EHg162o2mHxtCm4umNqHcbrTSEn.QXyIDO0wiNyAzNzEzW}
hacker@globbing~matching-with-:/challenge$





```


### New Learnings
Here i learned how to use the ? glob to specify the number of characters missing. Again it took me a few tries but i was able to understand and implement it well. 


 ## Matching with []
Next, we will cover []. The square brackets are, essentially, a limited form of ?, in that instead of matching any character, [] is a wildcard for some subset of potential characters, specified within the brackets. For example, [pwn] will match the character p, w, or n. For example:
```
hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_c
hacker@dojo:~$ ls
file_a	file_b	file_c
hacker@dojo:~$ echo Look: file_[ab]
Look: file_a file_b
```
Try it here! We've placed a bunch of files in /challenge/files. Change your working directory to /challenge/files and run /challenge/run with a single argument that bracket-globs into file_b, file_a, file_s, and file_h!

  ### Solve
  **Flag:** `pwn.college{c75kZvyWZtMBOEvuhiV30__9nRh.QXzIDO0wiNyAzNzEzW}`  

```
Connected!
hacker@globbing~matching-with-:~$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ ls
file_a  file_d  file_g  file_j  file_m  file_p  file_s  file_v  file_y
file_b  file_e  file_h  file_k  file_n  file_q  file_t  file_w  file_z
file_c  file_f  file_i  file_l  file_o  file_r  file_u  file_x
hacker@globbing~matching-with-:/challenge/files$ echo Look: file_[bash]
Look: file_a file_b file_h file_s
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[bash]
You got it! Here is your flag!
pwn.college{c75kZvyWZtMBOEvuhiV30__9nRh.QXzIDO0wiNyAzNzEzW}
hacker@globbing~matching-with-:/challenge/files$





```


### New Learnings
Here i learned how to use the [] glob to specify which characters i wanted to include in my search. I used file_[bash] because this comtained b, a, s and h which were the files i needed to select.


  ## Matching paths with []
Globbing happens on a path basis, so you can expand entire paths with your globbed arguments. For example:
```
hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_c
hacker@dojo:~$ ls
file_a	file_b	file_c
hacker@dojo:~$ echo Look: /home/hacker/file_[ab]
Look: /home/hacker/file_a /home/hacker/file_b
```
Now it's your turn. Once more, we've placed a bunch of files in /challenge/files. Starting from your home directory, run /challenge/run with a single argument that bracket-globs into the absolute paths to the file_b, file_a, file_s, and file_h files!

  ### Solve
  **Flag:** `pwn.college{oxKMis4gDJZm1781OVKyacxGKJj.QX0IDO0wiNyAzNzEzW}`  

```
Connected!
hacker@globbing~matching-paths-with-:~$ cd /challenge/files
hacker@globbing~matching-paths-with-:/challenge/files$ ls
file_a  file_d  file_g  file_j  file_m  file_p  file_s  file_v  file_y
file_b  file_e  file_h  file_k  file_n  file_q  file_t  file_w  file_z
file_c  file_f  file_i  file_l  file_o  file_r  file_u  file_x
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[bash]
You got it! Here is your flag!
pwn.college{oxKMis4gDJZm1781OVKyacxGKJj.QX0IDO0wiNyAzNzEzW}
hacker@globbing~matching-paths-with-:~$






```


### New Learnings
Here i basically had to do the previous question but without cding into the required directory first.



 ## Multiple globs

So far, you've specified one glob at a time, but you can do more! Bash supports the expansion of multiple globs in a single word. For example:
```
hacker@dojo:~$ cat /*fl*
pwn.college{YEAH}
hacker@dojo:~$
```
What happens above is that the shell looks for all files in / that start with anything (including nothing), then have an f and an l, and end in anything (including ag, which makes flag).

Now you try it. We put a few happy, but diversely-named files in /challenge/files. Go cd there and run /challenge/run, providing a single argument: a short (3 characters or less) globbed word with two * globs in it that covers every word that contains the letter p.

  ### Solve
  **Flag:** `pwn.college{cxEmlDKT7pslo8Uza9gDqdEQJVN.0lM3kjNxwiNyAzNzEzW}`  

```
Connected!
hacker@globbing~multiple-globs:~$ cd /challenge/files
hacker@globbing~multiple-globs:/challenge/files$ ls
amazing      fantastic   kind        pwning     uplifting   zesty
beautiful    great       laughing    queenly    victorious
challenging  happy       magical     radiant    wonderful
delightful   incredible  nice        splendid   xenial
educational  jovial      optimistic  thrilling  youthful
hacker@globbing~multiple-globs:/challenge/files$ /challenge/run /p
Error: your argument is too long! It must be 3 characters or less.
hacker@globbing~multiple-globs:/challenge/files$ /challenge/run *p*
You got it! Here is your flag!
pwn.college{cxEmlDKT7pslo8Uza9gDqdEQJVN.0lM3kjNxwiNyAzNzEzW}
hacker@globbing~multiple-globs:/challenge/files$


```


### New Learnings
Here i learned how to use multiple globs at once, each having specific conditions which helped me find the file i needed. I used *p* which means that the word must just contain the letter p in it. 


## Mixing globs

Now, let's put the previous levels together! We put a few happy, but diversely-named files in /challenge/files. Go cd there and, using the globbing you've learned, write a single, short (6 characters or less) glob that (when passed as an argument to /challenge/run) will match the files "challenging", "educational", and "pwning"!

  ### Solve
  **Flag:** `pwn.college{ANpAK6EUFD16KJQV5wDy8E5Vwvt.QX1IDO0wiNyAzNzEzW}`  

```
Connected!
hacker@globbing~mixing-globs:~$ /challenge/files
bash: /challenge/files: Is a directory
hacker@globbing~mixing-globs:~$ cd /challenge/files
hacker@globbing~mixing-globs:/challenge/files$ ls
amazing      fantastic   kind        pwning     uplifting   zesty
beautiful    great       laughing    queenly    victorious
challenging  happy       magical     radiant    wonderful
delightful   incredible  nice        splendid   xenial
educational  jovial      optimistic  thrilling  youthful
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [!pwn]8
Error: your argument is too long! It must be 6 characters or less.
hacker@globbing~mixing-globs:/challenge/files$ /challenge/files [cep]*
bash: /challenge/files: Is a directory
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*
You got it! Here is your flag!
pwn.college{ANpAK6EUFD16KJQV5wDy8E5Vwvt.QX1IDO0wiNyAzNzEzW}
hacker@globbing~mixing-globs:/challenge/files$




```


### New Learnings
This one took me a lot of time as i count figure out that all the words started with a different letter. Once i figured that out i could easily use [cep]* which meant that the words i need have to only start with the letters c, e and p.


## Exclusionary Globbing 

Sometimes, you want to filter out files in a glob! Luckily, [] helps you do just this. If the first character in the brackets is a ! or (in newer versions of bash) a ^, the glob inverts, and that bracket instance matches characters that aren't listed. For example:
```
hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_c
hacker@dojo:~$ ls
file_a	file_b	file_c
hacker@dojo:~$ echo Look: file_[!ab]
Look: file_c
hacker@dojo:~$ echo Look: file_[^ab]
Look: file_c
hacker@dojo:~$ echo Look: file_[ab]
Look: file_a file_b
```

Armed with this knowledge, go forth to /challenge/files and run /challenge/run with all files that don't start with p, w, or n!

NOTE: The ! character has a different special meaning in bash when it's not the first character of a [] glob, so keep that in mind if things stop making sense! ^ does not have this problem, but is also not compatible with older shells.

  ### Solve
  **Flag:** `pwn.college{QF7trfD5J4IKagW19AX_P6nb_yV.QX2IDO0wiNyAzNzEzW}`  

```
Connected!
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [!pwn]
Your expansion did not expand to the requested files (amazing beautiful
challenging delightful educational fantastic great happy incredible jovial kind
laughing magical optimistic queenly radiant splendid thrilling uplifting
victorious xenial youthful zesty).
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [^pwn]
Your expansion did not expand to the requested files (amazing beautiful
challenging delightful educational fantastic great happy incredible jovial kind
laughing magical optimistic queenly radiant splendid thrilling uplifting
victorious xenial youthful zesty).
Instead, it expanded to:
[^pwn]
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [^*pwn]
Your expansion did not expand to the requested files (amazing beautiful
challenging delightful educational fantastic great happy incredible jovial kind
laughing magical optimistic queenly radiant splendid thrilling uplifting
victorious xenial youthful zesty).
Instead, it expanded to:
[^*pwn]
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [!pwn*]
Your expansion did not expand to the requested files (amazing beautiful
challenging delightful educational fantastic great happy incredible jovial kind
laughing magical optimistic queenly radiant splendid thrilling uplifting
victorious xenial youthful zesty).
Instead, it expanded to:
[!pwn*]
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [pwn]*
Your expansion did not expand to the requested files (amazing beautiful
challenging delightful educational fantastic great happy incredible jovial kind
laughing magical optimistic queenly radiant splendid thrilling uplifting
victorious xenial youthful zesty).
Instead, it expanded to:
nice pwning wonderful
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [!pwn]*
You got it! Here is your flag!
pwn.college{QF7trfD5J4IKagW19AX_P6nb_yV.QX2IDO0wiNyAzNzEzW}
hacker@globbing~exclusionary-globbing:/challenge/files$




```


### New Learnings
Here i had to list out all the files that dont sart with p w or n. Since i understood the last one this one felt easy, i just had to use the ! or ^ glob and the letters pwn like [!pwn]* to exclude words starting with p w or n.


 ## Tab Completion


As tempting as it might be, using * to shorten what must be typed on the commandline can lead to mistakes. Your glob might expand to unintended files, and you might not spot it until the rm command is already running! No one is safe from this style of error.

A safer alternative when you are trying to specify a specific target is tab completion. If you hit tab in the shell, it'll try to figure out what you're going to type and automatically complete it. Auto-completion is super useful, and this challenge will explore its use in specifying files.

This challenge has copied the flag into /challenge/pwncollege, and you can freely cat that file. But you can't type the filename: we used some serious trickery to make sure that you must tab-complete it. Try it out!

```
hacker@dojo:~$ ls /challenge
DESCRIPTION.md  pwncollege
hacker@dojo:~$ cat /challenge/pwncollege
cat: /challenge/pwncollege: No such file or directory
hacker@dojo:~$ cat /challenge/pwn<TAB>
pwn.college{HECK YEAH}
hacker@dojo:~$
```

When you hit that tab key, the name will expand and you'll be able to read the file. Good luck!

  ### Solve
  **Flag:** `pwn.college{k5y7VCEqEl9eppzX3UtAmQ6-md5.0FN0EzNxwiNyAzNzEzW}`  

```
Connected!
hacker@globbing~tab-completion:~$ cat /challenge/
.bashrc         .init           DESCRIPTION.md  pwncollege​
hacker@globbing~tab-completion:~$ cat /challenge/pwncollege​
pwn.college{k5y7VCEqEl9eppzX3UtAmQ6-md5.0FN0EzNxwiNyAzNzEzW}
hacker@globbing~tab-completion:~$




```


### New Learnings
Tab feels much safer to use compared to the other globs as this ensures you pick the right file. It basically autocompletes the word youre going to type after giving it a few hints like the first few letters. This is ecpecially useful of all the files start with different letters so you can tab immediately after entering the first letter.


 ## Multiple options for tab completion


Consider the following situation:
```
hacker@dojo:~$ ls
flag  flamingo  flowers
hacker@dojo:~$ cat f<TAB>
```
There are multiple options! What happens?

What happens varies based on the specific shell and its options. By default bash will auto-expand until the first point when there are multiple options (in this case, fl). When you hit tab a second time, it'll print out those options. Other shells and configurations, instead, will cycle through the options.

This challenge has a /challenge/files directory with a bunch of files starting with pwncollege. Tab-complete from /challenge/files/p or so, and make your way to the flag!

  ### Solve
  **Flag:** `pwn.college{EzjKyTgE146WueWY9HMzJ8I86Ad.0lN0EzNxwiNyAzNzEzW}`  

```
Connected!
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwn
pwn                    pwncollege-family      pwncollege-flyswatter
pwn-college            pwncollege-flag        pwncollege-hacking
pwn-the-planet         pwncollege-flamingo
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwncollege -flag
cat: invalid option -- 'f'
Try 'cat --help' for more information.
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwn
pwn                    pwncollege-family      pwncollege-flyswatter
pwn-college            pwncollege-flag        pwncollege-hacking
pwn-the-planet         pwncollege-flamingo
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwncollege-f
pwncollege-family      pwncollege-flamingo
pwncollege-flag        pwncollege-flyswatter
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwncollege-fl
pwncollege-flag        pwncollege-flamingo    pwncollege-flyswatter
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwncollege-fla
pwncollege-flag      pwncollege-flamingo
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwncollege-flag
pwn.college{EzjKyTgE146WueWY9HMzJ8I86Ad.0lN0EzNxwiNyAzNzEzW}
hacker@globbing~multiple-options-for-tab-completion:~$





```


### New Learnings
This is the same as the last one but i just had to specify a bit more before tabbing as there were more than 1 file name starting with the letter.


## Tab Completion on commands


Tab completion is for more than files! You can also tab-complete commands. This level has a command that starts with pwncollege, and it'll give you the flag. Type pwncollege and hit the tab key to auto-complete it!

NOTE: You can auto-complete any command, but be careful: callous auto-completes without double-checking the result can wreak havoc in your shell if you accidentally run the wrong commands!

  ### Solve
  **Flag:** `pwn.college{oJnwsxnadnk98inb8hIcelF_th4.0VN0EzNxwiNyAzNzEzW}`  

```
Connected!
hacker@globbing~tab-completion-on-commands:~$ pwn
pwn               pwndbg            pwntools-gdb
pwncollege-12900  pwnstrip
hacker@globbing~tab-completion-on-commands:~$ pwncollege-12900
Correct! Here is your flag:
pwn.college{oJnwsxnadnk98inb8hIcelF_th4.0VN0EzNxwiNyAzNzEzW}
hacker@globbing~tab-completion-on-commands:~$



```


### New Learnings
Here i learned that i can use the tab complete glob to even autocomplete commands.
