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
