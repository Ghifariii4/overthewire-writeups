# Bandit26 -> 27: The Shell within a Shell

[Challenge](https://overthewire.org/wargames/bandit/bandit26.html)

## Level Description

This level is a continuation of Level 25. You are logged in as **bandit25**, and you have already escaped the "more" trap to get a shell. Now, you need to find the password for **bandit26**. However, the bandit26 user also has a restricted shell that immediately logs you out.

## The Process

I already had a shell as `bandit25` from the previous level. In the home directory, there was a file named `bandit26.sshkey`. I used this key to log in:

```bash
$ ssh -i bandit26.sshkey bandit26@localhost -p 2220

```

Just like before, I was instantly kicked out with a "Byebye!" message. I checked the `/etc/passwd` file to see what shell `bandit26` was using:

```bash
$ grep bandit26 /etc/passwd
# Output: bandit26:x:11026:11026:bandit26:/home/bandit26:/usr/bin/showtext

```

The shell was `/usr/bin/showtext`. I looked at that script:

```bash
$ cat /usr/bin/showtext
#!/bin/sh
export TERM=linux
more ~/text.txt
exit 0

```

It was the same "more" trick! I repeated the strategy from Level 25:

1. **Shrink terminal window** to a very small size.
2. **SSH** into bandit26.
3. When the `more` prompt appeared, I pressed `v` to enter **Vim**.
4. Inside Vim, I used a different trick to execute commands since I couldn't easily spawn a full shell:
```text
:e /etc/bandit_pass/bandit26

```


(The `:e` command in Vim stands for **edit**, allowing me to open and read any file I have permissions for.)

The password for Level 26 appeared right there in the editor.

## Password For the Next Level

`[SPOILER]`

## What I Learned

* **Vim as a File Browser**: I learned that once you escape into a text editor, you don't necessarily need a shell to read protected files; the editor itself can open them.
* **Persistent Restricted Shells**: I saw how the same vulnerability (using a pager as a shell) can be used to protect multiple accounts, and how the same exploit works across them.
* **The Power of :e**: I practiced using Vim commands to navigate the file system without a standard bash prompt.

## Helpful Reading Material

* Vim for reading files: [Vim Editing Commands](https://www.google.com/search?q=https://www.linux.com/training-tutorials/vim-101-editing-files-vim/)
* Understanding the /etc/passwd file: [Linux Passwd File Fields](https://www.cyberciti.biz/faq/understanding-etcpasswd-file-format/)
