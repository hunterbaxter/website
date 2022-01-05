---
title: Configuring Z shell (Zsh)
summary: quality of life changes to make the command line friendly
date: 2021-12-27T00:00:00-06:00
showToc: false
ShowReadingTime: true
tags: [linux,tech]
draft: false
---

Using the command line can be tiring at first if one is used to GUIs - one is constantly typing, and there are very few visual guides to assist until one gets in the habit of using [man](https://wiki.archlinux.org/title/Man_page) and [tldr](https://tldr.sh/) pages.
As a result, I am making this post to share my Zsh configurations (configurations that are not vi additions) with explanations. One can find my complete Zsh configuration in my [dotfiles repository](https://github.com/baxterhc/.dotfiles/tree/master/.config/zsh).

A couple of notes:
- .zshrc file contains the settings for Zsh, and is typically found at '~/.zshrc'.
- Some configuration options available are not unique to Zsh
- Zsh is the default shell on OSX, but bash is the default shell on most linux distributions (like fedora).

# Syntax Highlighting

Knowing one is wrong before executing is nice and is one of the many reasons the [language server protocol](https://en.wikipedia.org/wiki/Language_Server_Protocol) feature of text editor plugins and IDEs feels almost essential once one is used to it.
The command line does not have to be different.
To install this, [follow the instructions](https://github.com/zsh-users/zsh-syntax-highlighting/blob/master/INSTALL.md)
and then source 'zsh-syntax-highlighting.zsh' at the **bottom** (must be at the end) of one's '.zshrc' file.

``` zsh
source ~/.scripts/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
```

# Tricks
## Auto Change Directory
If one has to navigate through directories on a command line, it sounds ridiculous, but the three keypresses "cd<Space>" can feel unnecessary once repeated many times.
So, with Zsh, the "cd<Space>" can be implied, and one can type the directory's name instead.
``` zsh
setopt AUTO_CD
```

## Magic Space
Sometimes one forgets to use sudo.
Or, sometimes needs text before the previous command and after.
This situation is where Zsh's magic space comes into play.
Consider the following sequence where '%' prepends user input.
```
% ls
% !
```
after the exclamation, '<space>' is pressed, which changes the text in the current prompt
```
% ls
% ls
```

# Aliases
## Shortening Commands for Utilities
It can be annoying to have to repeatedly type the same command over and over (especially git), and some names are just long (looking at you, Zathura).
Instead of typing the whole command whenever one wants to use the command, one can pay the price of typing once by making an alias in .zshrc.
Below are a couple of aliases I use to type less, but I encourage one to expand them to more applications one frequently uses (I use Neovim and Zathura for most of my work).
``` zsh
alias \
    g="git"\
    ga="git add"\
    gc="git commit"\
    gr="git rm"\
    gs="git status"

alias \
    v="nvim"\
    vi="nvim"\
    z="zathura"
```

## Creating "Default" Settings for utilities
For some Unix utilities, colorized output is not on by default.
Instead, one needs to pass flags to turn on colorized output.
In addition, sometimes, there are flags one always wants to use.
One can prepend the alias with a backslash when using a command with an alias overriding it.


``` zsh
alias \
	ls="ls --color=auto --group-directories-first" \
	grep="grep --color=auto" \
	diff="diff --color=auto"
```

## Changing Directories
Suppose you keep your file system well organized.
This means your projects are nicely tucked away in an organized manner, likely a couple of levels deep.
When you open a terminal emulator, you want to get to these projects.
Do you have to type out the whole relative path from the home directory?
No!
One can use aliases to move into the directory quickly.
For example, here are some directory aliases I use

``` zsh
alias work="$HOME/Documents/professional/isis"
alias doc="$HOME/Documents"
alias dow="$HOME/Downloads"
```

# Adding to the shell path
Adding executables to the path is a fundamental aspect of using a shell.
If one wants to use a program, the shell must know where the executable is.
One can do this by appending the directory containing executable to the path.
Just make sure to export the path!

``` zsh
path+=('/usr/local/spark/bin') # spark
path+=('/usr/local/ampl') # ampl optimization solver
path+=('/home/baxterhc/.local/share/coursier/bin') # scala
path+=('/usr/local/share/openvswitch/scripts/') # mininet
path+=('/home/baxterhc/.local/bin') # for pip packages
export PATH
```
