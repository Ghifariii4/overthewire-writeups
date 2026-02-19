# Bandit03 -> 04: Hiding From You

[Challenge](https://overthewire.org/wargames/bandit/bandit3.html)

## Level Description

The password for the next level is stored in a hidden file in the **inhere** directory. Like a digital game of hide-and-seek, you need to find where it's tucked away!

## The Process

After logging in, I navigated into the `inhere` directory. I tried using the basic `ls` command, but to my surprise, the directory looked empty!

In Linux, files that start with a dot `.` are considered **hidden**. They don't show up with a regular list command. To see these "ghost" files, I had to use the `-a` (all) flag with `ls`.

Here is the sequence I used:

```bash
$ cd inhere
$ ls -a

```

Bingo! A file named `.hidden` appeared. I then used `cat` to read it:

```bash
$ cat .hidden

```

The password revealed itself immediately. Hide-and-seek over!

## Password For the Next Level

`[SPOILER]`

## What I Learned

* **Hidden Files**: I learned that any file starting with a dot `.` is hidden from the default view in Linux.
* **The 'all' Flag**: The `ls -a` command is essential for seeing everything inside a directory, including configuration files and hidden secrets.
* **Directory Navigation**: Moving between folders with `cd` is a basic but vital skill for exploring the system.

## Helpful Reading Material

* Understanding Linux file visibility: [Hidden Files and Directories in Linux](https://www.google.com/search?q=https://www.howtogeek.com/bash-guide-hidden-files-and-directories/)
* More `ls` tricks: [Mastering the ls Command](https://www.google.com/search?q=https://linuxjourney.com/lesson/ls-command)
