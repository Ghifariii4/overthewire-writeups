# Bandit06 -> 07: System-Wide Search

[Challenge](https://overthewire.org/wargames/bandit/bandit6.html)

## Level Description

The password for the next level is stored **somewhere on the server** and has all of the following properties:

* Owned by user **bandit7**
* Owned by group **bandit6**
* 33 bytes in size

## The Process

This time, the file wasn't just in a local folder—it was somewhere in the entire system. Searching the whole server means encountering thousands of files I don't have permission to read, which usually clutters the screen with "Permission denied" errors.

To find the password, I used the `find` command starting from the root directory `/`. I also used a clever trick to hide all the error messages by redirecting them to `/dev/null`.

Here is the command I used:

```bash
$ find / -user bandit7 -group bandit6 -size 33c 2>/dev/null

```

Here’s why it worked:

* `/`: Starts the search from the very top of the Linux file system.
* `-user bandit7` & `-group bandit6`: Filters for the specific owner and group.
* `2>/dev/null`: This sends all error messages (Standard Error) to a "black hole" so I only see the actual file path I'm looking for.

The command gave me one single path. I used `cat` on it, and the password was mine!

## Password For the Next Level

`[SPOILER]`

## What I Learned

* **Global Searching**: I learned how to search across the entire operating system, not just my home folder.
* **Redirection (2>/dev/null)**: This is a life-saver for cleaning up terminal output by ignoring errors.
* **Ownership Filters**: I learned that files can be found based on who owns them, which is a key part of Linux security.

## Helpful Reading Material

* Dealing with errors: [Understanding 2>/dev/null](https://www.google.com/search?q=https://www.brianstorti.com/understanding-shell-redirection/)
* Root directory explained: [The Linux Directory Structure](https://www.google.com/search?q=https://www.howtogeek.com/bash-guide-the-linux-directory-structure-explained/)
