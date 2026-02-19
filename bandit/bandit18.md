# Bandit17 -> 18: Spot the Difference

[Challenge](https://overthewire.org/wargames/bandit/bandit17.html)

## Level Description

There are two files in the home directory: **passwords.old** and **passwords.new**. The password for the next level is in **passwords.new** and is the only line that has been changed between the two files.

## The Process

When I logged in, I saw two large files. Looking through them manually would be a nightmare because they contain many similar-looking strings.

In Linux, there is a perfect tool for this called `diff`. It compares two files line by line and shows exactly what is different between them.

Here is the command I used:

```bash
$ diff passwords.old passwords.new

```

The output showed a few lines, but specifically, it pointed out the line that was removed from the old file and the new line added to the current file. The line marked with a `>` (indicating it belongs to the second file, `passwords.new`) was the password I needed.

## Password For the Next Level

`[SPOILER]`

## What I Learned

* **Comparing Files**: I learned that `diff` is the most efficient way to find changes between two versions of a file.
* **Interpreting Output**: I learned how to read `diff` results—specifically that `<` refers to the first file and `>` refers to the second.
* **Data Integrity**: This is a great real-world skill for checking what has changed in configuration files or code updates.

## Helpful Reading Material

* Comparing files: [How to use the diff command](https://www.geeksforgeeks.org/diff-command-linux-examples/)
* Visualizing changes: [Linux Diff and Patch guide](https://linux.die.net/man/1/diff)
