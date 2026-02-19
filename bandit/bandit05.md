# Bandit04 -> 05: Human Readable

[Challenge](https://overthewire.org/wargames/bandit/bandit4.html)

## Level Description

The password for the next level is stored in the only **human-readable** file in the **inhere** directory. Tip: if your terminal is messed up, try the `reset` command.

## The Process

I moved into the `inhere` directory and found a bunch of files named starting with a dash, like `-file01`, `-file02`, and so on. Most of these contain binary "garbage" that looks like a mess of symbols on the screen.

To find the right one without opening every single file manually, I used a wildcard `*` along with the `cat` command to peak into them. Since I knew from my previous notes that files starting with a dash need a `./` prefix, I ran:

```bash
$ cd inhere
$ cat ./-file*

```

Among the wall of weird symbols, one line stood out—it was a clean string of letters and numbers. That was our password!

## Password For the Next Level

`[SPOILER]`

## What I Learned

* **Identifying Data Types**: I learned that not all files contain text; some contain binary data that isn't meant to be read by humans.
* **Wildcard Power**: Using the asterisk `*` allowed me to process all files in the directory with a single command.
* **The 'file' Command**: While I used `cat` here, I also discovered that the `file` command is a professional way to check a file's type (e.g., "ASCII text") before opening it.

## Helpful Reading Material

* How to tell file types apart: [The Linux 'file' command](https://www.google.com/search?q=https://www.howtogeek.com/bash-guide-identifying-file-types/)
* Dealing with wildcards: [Bash Globbing Tutorial](https://linuxhint.com/bash_globbing_tutorial/)
