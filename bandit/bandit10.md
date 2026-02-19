# Bandit09 -> 10: Human Readable Strings

[Challenge](https://overthewire.org/wargames/bandit/bandit9.html)

## Level Description

The password for the next level is stored in the file **data.txt** in one of the few human-readable strings, preceded by several **'='** characters. This file is a binary file, which means if you try to `cat` it, your terminal will likely fill with unreadable symbols and beeps!

## The Process

When I tried to look at `data.txt`, I realized it wasn't a standard text file. It’s a binary file, which is usually meant for computers to read, not humans.

To solve this, I used the `strings` command. This handy tool scans binary files and pulls out only the sequences of printable characters. Since the clue mentioned the password is preceded by "==", I piped the output of `strings` into `grep` to filter for those equal signs.

Here is the command I used:

```bash
$ strings data.txt | grep "=="

```

The terminal filtered out all the binary junk and showed me a few lines containing `====`. One of them clearly displayed the password right next to the equal signs.

## Password For the Next Level

`[SPOILER]`

## What I Learned

* **Extracting Text from Binary**: I learned that the `strings` command is essential for finding "hidden" text inside non-text files.
* **Combining Filters**: Chaining `strings` with `grep` is a powerful way to find specific data in a sea of unreadable code.
* **Recognizing File Types**: I learned that just because a file has a `.txt` extension doesn't mean it's a plain text file—always check the content!

## Helpful Reading Material

* Finding text in binaries: [The Linux strings command](https://www.google.com/search?q=https://www.geeksforgeeks.org/strings-command-in-linux-with-examples/)
* More on Grep filtering: [Grep search patterns](https://linuxize.com/post/how-to-use-grep-command-to-search-files-in-linux/)
