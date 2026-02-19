# Bandit07 -> 08: The Millionth Word

[Challenge](https://overthewire.org/wargames/bandit/bandit7.html)

## Level Description

The password for the next level is stored in the file **data.txt** next to the word **millionth**. This file is quite large, so scrolling through it manually is out of the question!

## The Process

When I logged in and checked the directory, I saw `data.txt`. Opening a massive file with `cat` would flood the terminal and make it impossible to find anything.

To solve this, I used `grep`, a tool designed to search for specific patterns within text. By searching for the keyword "millionth," I could pull out the exact line containing the password.

Here is the command I used:

```bash
$ grep "millionth" data.txt

```

The output showed the word "millionth" followed by a string of characters. That string was the password I needed to move forward.

## Password For the Next Level

`[SPOILER]`

## What I Learned

* **Efficient Searching**: I learned that `grep` is the go-to tool for finding specific information inside large text files.
* **Pattern Matching**: Using a simple keyword as a search pattern can save a huge amount of time compared to manual searching.
* **Handling Large Data**: In security and administration, you often deal with giant logs or data files; knowing how to filter them is a vital skill.

## Helpful Reading Material

* Basic Grep usage: [How to Use Grep Command in Linux](https://linuxize.com/post/how-to-use-grep-command-to-search-files-in-linux/)
* Fast text processing: [Grep Command Tutorial with Examples](https://www.geeksforgeeks.org/grep-command-in-unixlinux/)
