 # Data Manipulation
  ## Translating Characters

One of the purposes of piping data is to modify it. Many Linux commands will help you modify data in really cool ways. One of these is tr, which translates characters it receives over standard input and prints them to standard output.

In its most basic usage, tr translates the character provided in its first argument to the character provided in its second argument:

```
hacker@dojo:~$ echo OWN | tr O P
PWN
hacker@dojo:~$
```

It can also handle multiple characters, with the characters in different positions of the first argument replaced with associated characters in the second argument.

```
hacker@dojo:~$ echo PWM.COLLAGE | tr MA NE
PWN.COLLEGE
hacker@dojo:~$
```

Now, you try it! In this level, /challenge/run will print the flag but will swap the casing of all characters (e.g., A will become a and vice-versa). Can you undo it with tr and get the flag?


  ### Solve
  **Flag:** `pwn.college{EZWpuTXZreOOf6QTFp5gA89r1o4.01MxEzNxwiNyAzNzEzW}`  

```

Connected!
hacker@data~translating-characters:~$ /challenge/run
Your case-swapped flag:
PWN.COLLEGE{ezwPUtxzREooF6qtfP5Ga89R1O4.01mXeZnXWInYaZnZeZw}

hacker@data~translating-characters:~$ echo PWN.COLLEGE | tr PWN.COLLEGE pwn.college
pwn.college
hacker@data~translating-characters:~$ /challenge/run | tr abcdefghijklmnopqrstuvwxyz ABCDEFGHIJKLMNOPQRSTUVWXYZ
YOUR CASE-SWAPPED FLAG:
PWN.COLLEGE{EZWPUTXZREOOF6QTFP5GA89R1O4.01MXEZNXWINYAZNZEZW}

hacker@data~translating-characters:~$ /challenge/run | tr abcdefghijklmnopqrstuvwxyz ABCDEFGHIJKLMNOPQRSTUVWXYZ | tr ABCDEFGHIJKLMNOPQRSTUVWXYZ abcdefghijklmnopqrstuvwxyz
your case-swapped flag:
pwn.college{ezwputxzreoof6qtfp5ga89r1o4.01mxeznxwinyaznzezw}

hacker@data~translating-characters:~$ /challenge/run | tr 'abcdefghijklmnopq
rstuvwxyz ABCDEFGHIJKLMNOPQRSTUVWXYZ' 'ABCDEFGHIJKLMNOPQRSTUVWXYZ abcdefghijklmnopqrstuvwxyz'
yOUR CASE-SWAPPED FLAG:
pwn.college{EZWpuTXZreOOf6QTFp5gA89r1o4.01MxEzNxwiNyAzNzEzW}

hacker@data~translating-characters:~$





```


### New Learnings
Here i swapped all the lower cases to capital letters and vice versa using the tr (translate) command.


  ## Deleting characters

tr can also translate characters to nothing (i.e., delete them). This is done via a -d flag and an argument of what characters to delete:

```
hacker@dojo:~$ echo PAWN | tr -d A
PWN
hacker@dojo:~$
```

Pretty simple! Now you give it a try. I'll intersperse some decoy characters (specifically: ^ and %) among the flag characters. Use tr -d to remove them!


  ### Solve
  **Flag:** `pwn.college{EUX467XssK4UUSNZR1uPSxqbKuP.0FNxEzNxwiNyAzNzEzW}`  

```
Connected!
hacker@data~deleting-characters:~$ /challenge/run
Your character-stuffed flag:
p%w^n^%.^%c%o^%l^%l^%eg%e%{^%E^%U^X^%4^%67^X^s^%s^%K^4%U^USNZ^R^%1^%u^P^Sxq^%b^K%uP^%.0%F^%N%xE^z%N%x^%w%i^%Ny^Az^N%z^%E^z^%W^%}%^
hacker@data~deleting-characters:~$ /challenge/run | tr -d '^' '%'
tr: extra operand ‘%’
Only one string may be given when deleting without squeezing repeats.
Try 'tr --help' for more information.
hacker@data~deleting-characters:~$ /challenge/run | tr -d ^ %
tr: extra operand ‘%’
Only one string may be given when deleting without squeezing repeats.
Try 'tr --help' for more information.
hacker@data~deleting-characters:~$ /challenge/run | tr -d ^%
Your character-stuffed flag:
pwn.college{EUX467XssK4UUSNZR1uPSxqbKuP.0FNxEzNxwiNyAzNzEzW}
hacker@data~deleting-characters:~$






```


### New Learnings
Here i used the -d command to delete all the ^'s and %'s from the flag. I learned that you can just type the characters side by side instead of putting them in brackets.


  ## Deleting newlines

A common class of characters to remove is a line separator. This happens when you have a stream of data that you want to turn into a single line for further processing. You can specify newlines almost like any other character, by escaping them:

```
hacker@dojo:~$ echo "hello_world!" | tr _ "\n"
hello
world!
hacker@dojo:~$
```

Here, the backslash (\) signifies that the character that follows it is a standin for a character that's hard to input into the shell normally. The newline, of course, is hard to input because when you typically hit Enter, you'll run the command itself. \n is a standin for this newline, and it must be in quotes to prevent the shell interpreter itself from trying to interpret it and pass it to tr instead.

Now, let's combine this with deletion. In this challenge, we'll inject a bunch of newlines into the flag. Delete them with tr's -d flag and the escaped newline specification!

Fun fact! Want to actually replace a backslash (\) character? Because \ is the escape character, you gotta escape it! \\ will be treated as a backslash by tr. This isn't relevant to this challenge, but is a fun fact nonetheless!


  ### Solve
  **Flag:** `pwn.college{0GFIEKQgcHZuk9OtWvkxjQvVB5b.0VNxEzNxwiNyAzNzEzW}`  

```

Connected!
hacker@data~deleting-newlines:~$ /challenge/run
Your line-split flag:
p
wn
.
c
ol
le
ge
{
0GF
IE
K
Q
gcHZ
u
k
9
O
tWvk
xjQ
v
V
B5b.0V
N
x
Ez
N
xw
i
N
yAzN
zE
z
W}

hacker@data~deleting-newlines:~$ /challenge/run | tr -d "\n"
Your line-split flag: pwn.college{0GFIEKQgcHZuk9OtWvkxjQvVB5b.0VNxEzNxwiNyAzNzEzW}
hacker@data~deleting-newlines:~$


```


### New Learnings
Here i deleted all the spaces (\n) by using the -d command.


  ## Extracting the first lines with head

In your Linux journey, you'll experience situations where you need to grab just the early output of very verbose programs. For this, you'll reach for head! The head command is used to display the first few lines of its input:

```
hacker@dojo:~$ cat /something/very/long | head
this
is
just
the
first
ten
lines
of
the
file
hacker@dojo:~$
```

By default, it shows the first 10 lines, but you can control this with the -n option:

```
hacker@dojo:~$ cat /something/very/long | head -n 2
this
is
hacker@dojo:~$
```

This challenge's /challenge/pwn outputs a bunch of data, and you'll need to pipe it through head to grab just the first 7 lines and then pipe them onwards to /challenge/college, which will give you the flag if you do this right! Your solution will be a long composite command with two pipes connecting three commands. Good luck!


  ### Solve
  **Flag:** `pwn.college{4uCAYvYHdpQdWgQ7wtjf5X13UFv.0lNxEzNxwiNyAzNzEzW}`  

```

Connected!
hacker@data~extracting-the-first-lines-with-head:~$ cat /challenge/pwn | head -n 7 | /challenge/college
Invalid codes!
hacker@data~extracting-the-first-lines-with-head:~$ /challenge/pwn | head -n 7 | /challenge/college
Congratulations, you piped the right codes!
pwn.college{4uCAYvYHdpQdWgQ7wtjf5X13UFv.0lNxEzNxwiNyAzNzEzW}
hacker@data~extracting-the-first-lines-with-head:~$



```


### New Learnings
Here i piped the /challenge/pwn command and used the head command to only print me the first 7 files. I then piped this back into /challenge/collage which gave me the flag .


 ## Extracting specific sections of text


Sometimes, you want to grab specific columns of data, such as the first column, the third column, or the 42nd column. For this, there's the cut command.

For example, imagine that you have the following data file:

```
hacker@dojo:~$ cat scores.txt
hacker 78 99 67
root 92 43 89
hacker@dojo:~$
```

You could use cut to extract specific columns:

```
hacker@dojo:~$ cut -d " " -f 1 scores.txt
hacker
root
hacker@dojo:~$ cut -d " " -f 2 scores.txt
78
92
hacker@dojo:~$ cut -d " " -f 3 scores.txt
99
43
hacker@dojo:~$
```

The -d argument specifies the column delimiter (how columns are separated). In this case, it's a space character. Of course, it has to be in quotes here so that the shell knows that the space is an argument rather than a space separating other arguments! The -f argument specifies the field number (which column to extract).

In this challenge, the /challenge/run program will give you a bunch of lines with random numbers and single characters (characters of the flag) as columns. Use cut to extract the flag characters, then pipe them to tr -d "\n" (like the previous level!) to join them together into a single line. Your solution will look something like /challenge/run | cut ??? | tr ???, with the ??? filled out.


  ### Solve
  **Flag:** `pwn.college{4XxOksapFTDRQ6nIYGRmbFtl1c0.01NxEzNxwiNyAzNzEzW}`  

```

Connected!
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run
10269 p
4468 w
26733 n
26776 .
29991 c
25535 o
13393 l
22789 l
31615 e
2641 g
22003 e
24526 {
23550 4
5621 X
17857 x
1481 O
3060 k
105 s
10995 a
21887 p
5099 F
10839 T
22098 D
24246 R
5757 Q
27322 6
29126 n
6598 I
16195 Y
19973 G
20218 R
7648 m
4504 b
10959 F
5366 t
20569 l
15261 1
21498 c
32142 0
2913 .
18156 0
19649 1
8335 N
14136 x
27579 E
25871 z
31157 N
1702 x
2165 w
30391 i
32033 N
12024 y
7538 A
15480 z
31785 N
3487 z
30139 E
24713 z
19339 W
5353 }

hacker@data~extracting-specific-sections-of-text:~$ /challenge/run | cut -d " " -f 1 | tr -d "\n"
31594108672813615939107046470212541982519798203112022599021205139731098432112186402642332003903139858687188220702220516166294811244565292471158581999217131540376173641430920771279691856511170182793016420164156943171323092186216150320221670223274481653225224314412616920656425113033
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run | cut -d " " -f 2 | tr -d "\n"
pwn.college{4XxOksapFTDRQ6nIYGRmbFtl1c0.01NxEzNxwiNyAzNzEzW}
hacker@data~extracting-specific-sections-of-text:~$



```


### New Learnings
Here when i ran the command /challenge/run it printed out a bunch of lines where the flag part was always in the 2nd column so i could use ( cut -d " " -f 2) to just get the 2nd column and also the (tr -d "\n") command to join them together by deleting the empty lines between them.


  ## Sorting data


Files (or output lines of commands) aren't always in the order you need them! The sort command helps you organize data. It reads lines from input (or files) and outputs them in sorted order:

```
hacker@dojo:~$ cat names.txt
  hack
  the
  planet
  with
  pwn
  college
hacker@dojo:~$ sort names.txt
  college
  hack
  planet
  pwn
  the
  with
hacker@dojo:~$
```

By default, sort orders lines alphabetically. Arguments can change this:

-r: reverse order (Z to A)
-n: numeric sort (for numbers)
-u: unique lines only (remove duplicates)
-R: random order!

In this challenge, there's a file at /challenge/flags.txt containing 100 fake flags, with the real flag mixed among them. When sorted alphabetically, the real flag will be at the end (we made sure of this when generating fake flags). Go get it!

  ### Solve
  **Flag:** `pwn.college{UgQrOopfNbzKNatYU_eufyidU5x.0FM0MDOxwiNyAzNzEzW}`  

```

Connected!
hacker@data~sorting-data:~$ sort -r /challenge/flags.txt
pwn.college{UgQrOopfNbzKNatYU_eufyidU5x.0FM0MDOxwiNyAzNzEzW}
pwn.college{UgQrOopfNbzKNatYU_eufyidU5x.0FM0MDOxwiNyAzNzEzW}
pwn.college{UgQrOopfNbzKNatYU_eufyidU5x.0FM0MDOxwiNyAzNyDzV}
pwn.college{UgQrOopfNbzKNatYU_eueyidU5x.0FM0MCOxwiNyAzNzEzW}
pwn.college{UgQrOopfNbzKNatXU_eufyidU5x.0FM0MDOxwiNyAzNzEzW}
pwn.college{UgQrOopfNbzKNasYU_eufyicU5x.0FM0MDOxwiNyAzNyEzW}
pwn.college{UgQrOopfNbzJNatYU_eufyicU5x.0FM0MDOxwiNyAzNzEzW}
pwn.college{UgQrOopeNbzKNatYU_eufyidU5w.0FM0MDOxwiNyAzNzEzW}
pwn.college{UgQrOoofNbzKNatYU_eufxidU5x.0FM0MDOxwiNyAzNzEzW}
pwn.college{UgQqOnpfNbyKMatYU_eteyhdU5x.0FM0MDOxwiNxAzNzEyW}
pwn.college{UgPrOnofNazKNatYU_dufxidU5x.0FM0MCOxwiNxAzNzEzV}
pwn.college{UfQrOopfNbzKNatYU_eufyidU5x.0FL0MDNxwiNyAzMzEzV}
pwn.college{UfQrOopfNbzKNasYU_etfyidU5x.0FM0MDOwwhNyAzNzEzW}
pwn.college{UfQrOnpfNbzKNatYU_eufxidU5x.0FM0MDOxviNyAzNzEzW}
pwn.college{TgQrOoofNbyKNasYT_dtfyhdT5w.0FM0MDOxwiNyAzNyEyV}
pwn.collegd{UfQrOopfNazJMatYU_eufyidU5x.0FM0MCOwwhMyAzNzEzW}
pwn.collefe{UgQrOopfNbzKNatYU_eufyidU5x.0FM0MDOxwiNyAzNzEzW}
pwn.collefe{UgPrOopeNbzKNatYT_dufyidU5x.0FM0MDOxwiNyAzNzEzW}
pwn.collefe{UfQrOopeMbyKNatYT_eufyidU4w.0FM0MDOxwiNyAzMzDzV}
pwn.colldge{UgQrOopfNbyKNatYT_eufyidU5x.0FM0MDOxwiNyAzNzEzW}
pwn.colldge{UgQqOopfNbyKNatYU_dueyidT5w.0FM0LDOwwhNyAzNzEzW}
pwn.colldgd{UfQrOopeNbzKNatYT_eufyidU5x.0EM0LDOxwiNyAzNzDzW}
pwn.colldfe{UgQrOopfNbzJNasYU_eteyidU5w.0EM0LDNwviMyAyNzEzW}
pwn.colkege{UgQrOopfNbyKNasYU_eufyhdU5x.0FM0LDOxwiNyAzNzEyW}
pwn.colkege{UgPrOoofNazJNatYU_eufxidU5w.0FL0MCOxvhNyAyMyDyW}
pwn.colkegd{TgQrOopfNbzKNasYU_dtfyicT5x.0FL0MCOxwiNyAzNzEyW}
pwn.colkegd{TgQqOopfNbyKNasYU_eueyicU5x.0FL0MDOwwhNyAzNzEyW}
pwn.colkefe{UgQqOoofNazKNatYU_dufyidU5x.0FM0MDOxwhNxAzNzEzW}
pwn.colkefe{TgPqNoofNazKMatYT_dtfxidT5x.0FM0MCOwviNxAzNzEzW}
pwn.colkefd{TfQqOnpfNazKNasXT_etfyhdU4x.0FM0MDNxwiNyAzNyDyW}
pwn.coklege{UgQrOopfNbzKNasYU_dufyidU5x.0FM0MDOxwiNyAzNzEzW}
pwn.coklege{UfQrOoofNbzKNatYU_eufxidT5x.0FM0LDOxwiMyAyNyDyV}
pwn.coklefe{UgQrOopfNbzKNatYT_eufxhcU4x.0FM0MDOxwiNyAyNyEzV}
pwn.coklefe{UgQrOopfNbzKNasYT_eufyidU5x.0FM0MDOxwiNyAzNyEzW}
pwn.cokkege{TgQrOopfNbzKNatYU_eufyicU5w.0FM0LDOxwiNyAzNzEzW}
pwn.cnllege{UgPrOopeNbzKNatXU_dtfyidU5w.0FM0LDOwwiNyAyNzDzV}
pwn.cnllege{UfQrOopeNbzKMatYU_dufyidU5x.0FL0MDOxviNyAyMzEzW}
pwn.cnllefd{UgQrOopfNbzKNatYU_eufyidT5x.0EM0MDOxwiNyAzMyEzW}
pwn.cnlldge{UgQqOopeNbzKNatYU_eufyhdU5x.0FL0MCOwwiNyAzNzEzW}
pwn.bollege{UgQrNnpfNbyKNatXT_eufyidU5w.0FM0MCNxwiNyAyMzDyW}
pwn.bollege{TgQrOopfNbzKNatYU_eueyhdU5x.0EM0MDOxwiNyAzNzDyW}
pwn.bollege{TgQrOooeNbyKNasYU_dufxidT5x.0FL0MDOxwiNyAzNyDyW}
pwn.bollegd{TgQrOopfNbzKMatYU_eufyidU5x.0FL0MDOxviNyAzNyEzW}
pwn.bollegd{TgQrOnpfNbzKMatXU_eufyidU5x.0FM0MDOxwiNxAzNzEyV}
pwn.bollefe{TfQrOoofMbzKMatXU_euexhdU5x.0FM0LDNxwiNxAzMzEyW}
pwn.bollefd{UfQrNopeNbyKNatXU_etfyicU5w.0EL0LDOxviNyAzNzDzV}
pwn.bolkege{UgQqNopfNazKNasYU_eteyhdU5x.0EM0MDOxwiNyAzNyEzW}
pwn.bolkefe{TgQqOopeNazKNatXU_eufxhdU5w.0EM0MDOxwiNxAzNzEyW}
pwn.bolkdfd{TfQqOnpfNbzJNatYU_etfyidT5w.0FL0MCOwwiNyAyNzEyW}
pwn.bnklefd{UfPrNopfNazJNatXT_dufyidU5w.0FM0MCOxwiNxAzNzEzW}
pwm.college{UgPrOopfNbzKNatYU_eufyidU5x.0FM0MCOxwiNyAzNzEzW}
pwm.collegd{UgQrOopfNbzKNatXU_eufyidU5x.0FM0MDNwviNyAzNzDzW}
pwm.collegd{UgQrOooeNbyKNatYU_eufyidU5x.0FM0MDNxwiNyAzNzEzW}
pwm.collegd{UgPrOopfMbzJMatXT_eufyidU4x.0FM0MDOxvhNyAyMyEyV}
pwm.collefe{UgQrNnpfNbzKNatYU_etfyicU5x.0FL0MDOwwhNyAyNzEyW}
pwm.colldgd{UgPrNnpfMbzKMatXT_etfxhdU4w.0EL0MCNxwiNyAyMzEyV}
pwm.colkdge{UfQqOopfMbzKNatYU_eteyicU5x.0FM0MCOxviMyAzNzEzW}
pwm.cokkegd{UfPqOopfNbzJNasYT_eufxhdU5x.0FM0MCOxwhNxAyMzEzV}
pwm.cokkdge{UfQrNopeMbzKNatYU_eufyhcT5x.0FM0LDNwviNyAzMzDzV}
pwm.cnklege{TgQrNopeNayKNatXU_eufyicU5w.0FL0MDOxwiMyAzNzEyW}
pwm.cnklege{TgPqNooeNbzKMatYU_eufxicU5w.0FM0MCOxviNxAyMyEzW}
pwm.cnkldgd{UgPrNopfNbyKNatYU_eueyhdU5x.0FM0MCOwvhNyAzNzEzV}
pwm.bollegd{UgPqOopfNbyJNatYU_eueyidU5x.0FM0MDOxwiMxAyNzEyV}
pwm.boklege{UgPqOnofNazKNatYU_eufyidU5x.0FL0LCNxviNyAzNyEyW}
pwm.bnllege{UfPrOnoeNazKNatYU_etfyidU5x.0FM0MDOwviMyAzNyDzW}
pwm.bnklefd{UgPqOopfMbzJNasYU_eueyidT5x.0FL0MDOwwiNyAyNyEyV}
pvn.college{TgQrOnpfNbzKMasYT_eufyicU5x.0FM0MDOxwiMxAzNzEzW}
pvn.collefd{TfQrNopeNbyJNatYU_etfyidU5x.0FM0MDOwvhNyAzNzEzW}
pvn.cokldgd{TgPqNnpfMbzKNatYU_eueyhdU5x.0EM0MCOwwiNxAzNzDzW}
pvn.cokkefe{UfQrOopfNbzKNatYU_eufyhdU5x.0FL0MDNwviNyAzMzEzW}
pvn.cnllege{UgQqNnpfNazKNasYU_eueyhdU5x.0FM0LDOwwiNyAyNyEzV}
pvn.cnlkege{TfPrNnofNbzKMasXU_dufxidU4w.0EM0MDOxwhNxAyNzEzW}
pvn.cnklege{UfQrOopfNbzKNatYU_dufyicT5x.0FM0LDOxviNyAzNzDzW}
pvn.bolldge{UfPqNopeNbyKNasYU_dtfyicU5x.0EM0MDNwwhNyAyMyEyW}
pvm.college{UgQrOopfNbyKNasYT_eufyicU5w.0FM0MDOxviNxAzNzEzW}
pvm.college{UfQrOopfNayJMatXT_eufyicU4w.0EL0LDNwwiNyAyMzDzV}
pvm.college{TfQrOopfNbyKNasYU_etfyidU5x.0FM0MDOxwiNyAzNyEzW}
pvm.colkege{UgQrOoofNazKMatYU_eufyidU5x.0FM0MCNxwhNyAyNzEyW}
pvm.colkefe{UfQrNopeNayKNasYT_eueyhcU5w.0FM0LCOxwiNyAzNyDzW}
pvm.cokkdge{UfPrOopfMayKNatXU_dufxidU4x.0FL0LDOxwiNxAyNyDyV}
pvm.cnllegd{UfQrOnoeMbyKNatYU_euexidU5x.0FL0MDOxviNyAzNzEzW}
own.college{UgQrOopfNbzKNatYU_eufyidU5w.0EM0MDOxwiNyAzNzEzW}
own.college{UfQrOopeNbyJNatYT_dtfyicU5x.0FM0MDOxwiNyAyNzEzW}
own.collegd{UgQrOopfNbyKNatYU_eufyidU5x.0FM0MDOxwiNxAzNzEzW}
own.colkege{UgQrOopfNazKMatXU_dufxhdU5x.0FL0MDOxviMyAyMzEzV}
own.colkefd{UgQrOnpeNbzKMatYT_dufxhdT5x.0FL0LCNxwhMyAyNyEzW}
own.cokkdfd{UgPrOnpfNbzKNatYU_eufxidU5x.0FM0MDOxwiNyAzMzEyV}
own.cnlldgd{UfPrOopfNbzKNatYT_eufxhdU5w.0FM0MCOxwiMyAyNzEzW}
own.bollege{UgQrOopeNbyKNatYU_eufyicU4x.0FL0MCOwwiMxAyNyDyV}
own.bollege{UgPrNopeNazKNatYU_eufxidT5x.0EM0LDOxwhMyAzNyEzW}
own.bnllege{UgPrNopfNbyKNasYU_eueyidU4x.0FL0MDNwwiMxAzMyDzW}
owm.coklege{UgQrNopeNbzJNasYT_etfxidT5x.0FL0LDOxwiMxAzNzEzV}
owm.cnllefd{UgPrOooeNbzJNatXU_eufyicT5x.0FL0LDNxviNxAzNyEyW}
owm.cnlkege{TfQqOnofMbzKNatYT_eufyhdU5x.0FM0LDNwwhNxAzMzEzV}
ovn.cokkege{UgQrOnpfNazKMatYT_etfyidU5x.0FM0MCOxwhMxAzMyEyW}
ovn.cokkege{UgQqNnofNbzKNatYT_dueyhcU4w.0FL0LCOwviMyAyNyEzW}
ovn.cnllefe{UgQqOnpfNbyKNasYU_eufyidT4x.0EM0MDNwwhNxAzMzEzW}
ovn.cnlldge{UgPrOopfNbyKNatXU_dufyidT5w.0FM0MDOxvhNyAyMzEyV}
ovn.bolldge{UgPrNnpfNbyKNasYU_eufyicT5w.0FL0MDOxwiNxAyMyDyW}
ovm.cnlkdgd{TgQqNnpfNbzJMatYT_eufyidU4w.0FM0MDNwvhNxAzNzDyW}
ovm.bnllegd{UgPrOooeMbzKNatXT_eufxhdU5x.0FM0MDOwwiMxAzMyEzW}
hacker@data~sorting-data:~$ sort -r /challenge/flags.txt | head -n 1
pwn.college{UgQrOopfNbzKNatYU_eufyidU5x.0FM0MDOxwiNyAzNzEzW}
hacker@data~sorting-data:~$


```


### New Learnings
Here i used sort -r to print out all the flags in reverse alphabetic order so it printed it out as the first flag. But then i realized that i didnt need all the other flags so i combined it with the head command by doing (head -n 1), to only get that 1 flag.
