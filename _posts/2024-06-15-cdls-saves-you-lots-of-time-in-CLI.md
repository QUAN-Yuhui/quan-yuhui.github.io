---
title:  "cl saves you lots of time in CLI"
date:   2024-06-15 12:30:00 +0800
categories: Tech
tags:
  - UNIX/Linux
  - CLI
---
UNIX/Linux command line interface (CLI) is widely used by people. I believe that `cd` and `ls` are two most frequently used commands and they are usually used together when you change the directory and then show its content.

It would be great that we can use a single command to finish these two tasks at once. Here comes out `cl`. Suppose you are using Bash shell, you will see something like below in `~/.bashrc` file:

```
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
```

This lets the shell source `~/.bash_aliases` file （if it exists) every time the shell session starts. To create a new command `cl` to save your time, first create `~/.bash_aliases` if it doesn't exist. You may use
```
$ touch ~/.bash_aliases
```
to create this file. Then, in the `~/.bash_aliases` file, add the following:
```
cl()
{
  cd $@;
  ls;
}
```
This is basically a shell function called cl. `$@` means all arguments.

After all these steps, don't forget to source it 
```
$ . ~/.bash_aliases
```
Bingo! Now you can use `cl`. You may try this:
```
$ cl ~
```
If all goes well, you will change to the home directory and list its content.