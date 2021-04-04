---
layout: post
title:  "The most productive shell commands and command line tricks"
permalink: /shell-commands/
tags:  Command-line Shell Bash Zsh
date: 04-04-2021
---

When developing software, no matter what technology you are working with there is no way around using the command line when you want to be a productive developer.

This a list of my favorite and most used shell commands and tricks that I learned over the years. I'm sure you know some of them already so feel to skip the ones you know but others might bring you a productivity boost and lets you show off your 1337 h4x0r $killz in front of your n00b colleagues.

_Disclaimer: I use these commands on MacOS with Z Shell(Zsh) in Iterm2. As long as you are running a bash-like shell on a Unix & -like OS these commands should work for you as well. If you have a more exotic set up, you probably know your way around the shell to make these work yourself. If you run Powershell on Windows: Good Luck!_

# cd -

You probably know that you can use cd to change into a certain directory.
But did you know you can use the dash (-) as an argument to go back to the previous directory?
```
$ cd /home
~> home
$ cd /my_dir
~> /my_dir
$ cd -
~> /home
```

For a larger directory history check out [pushd and popd](https://medium.com/r/?url=https%3A%2F%2Funix.stackexchange.com%2Fquestions%2F77077%2Fhow-do-i-use-pushd-and-popd-commands).


# Shell History
Probably the most used _shell trick_ I use is to press the `up arrow` (successively) to select the last commands of my shell history.
Accompanied by `ctrl + r` (successively) to reverse search through my shell history by a keyword in LRU order.

## !!
You can also include `!!` in your command, and it gets substituted with the previously executed command.

```
$ apt-get install unicorn-factory
> [...] Permission denied
$ sudo !!
> sudo apt-get install unicorn-factory
```


## !:[index]

Or you can select just parts of the last command by including `!:[index]` in your command and the word at the index `[index]` in the previous command gets inserted.

```
$ echo hello world
> hello world
$ echo !:1
> hello
```

You can even select ranges with [index]-[index] ...

```
$ echo live long and prosper
> live long and prosper
$ echo !:3-4
> and prosper
```


## !^ !$
There are also shortcuts for the first(!^), and the last(!$) parameters of the previous command.

```
$ echo live long and prosper
> live long and prosper
$ echo !^ !$
> live prosper
```


# Editing the current line

This can be especially useful when you have just selected a command from the history which needs some slight change.
You can move your cursor to the beginning of the line by pressing `ctrl + a` and to the end of it by pressing `ctrl + e` (remember: e for _e_nd and a for, erm ... the beginning of the alphabet(?))

Additionally:

* `ctrl + w` cuts the word to the left of the cursor
* `alt + d` cuts the word to the right of the cursor
* `ctrl + k` cuts everything to the right of the cursor
* `ctrl + u` cuts everything to the left of the cursor
* `ctrl + y` pastes back what you have just cut

## ctrl + x + e
If you realize you actually need to make a bigger edit or write a longer command you can also switch to your editor and take current line with you.

```
$ you are typing this really long command, maybe with some loop or some complex parsing logic and then realize you need more editing power so you press ctrl + e + x
BOOOM!
VIM(or Nano or VI etc.) opens with your command you had typed so far already in the buffer
```

## Paste modified command from history

Instead of retrieving the last command and then modifying it in two separate steps you can also do it in one step.

`^x^y` gives you the previous command with x replaced by y

```
$ gti status
> Command 'gti' not found,
$ ^gti^git
> git status
```


# Handling multiple files with one command
You might have used commands like cp or mv before to handle files.
One of my favorite shortcut is the {} parameter expansion.
By using {} you instruct your shell to expand each value on the curly brackets.

```
$ mv hello_world.{js,html} static
```
This command moves both the hello_world.js file and the hello_world.html file without needing to type hello_world. twice.
You can also use ranges…
The following command moves 5 files (file1.png, file2.png, file3.png, file4.png, and file5.png) to the backup/ directory.

```
$ mv file{1..5}.png backup/
```

---
As there are many more commands that will help you be productive I will be constantly updating this list when I come across new jewels so you might want to bookmark this article for future references.
In the mean time share your favorite command in the comments.
