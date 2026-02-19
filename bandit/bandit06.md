# Bandit05 -> 06: The Great Search

[Challenge](https://overthewire.org/wargames/bandit/bandit5.html)

## Level Description

The password for the next level is stored in a file somewhere under the **inhere** directory and has all of the following properties:

* Human-readable
* 1033 bytes in size
* Not executable

## The Process

This level felt like looking for a needle in a haystack! Inside the `inhere` directory, there were multiple folders and dozens of files. Checking each one manually would have taken forever.

To solve this, I used the `find` command. It is a powerful tool that allows you to search for files based on specific attributes like size and type. I combined the clues from the description into a single command:

```bash
$ cd inhere
$ find . -type f -size 1033c ! -executable

```

Here is a breakdown of what those flags do:

* `.`: Search in the current directory.
* `-type f`: Look for regular files only.
* `-size 1033c`: Look for a file exactly 1033 bytes (the `c` stands for bytes).
* `! -executable`: The exclamation mark means "not," so this looks for files that are not executable.

The command pointed me directly to one specific file. I used `cat` on that path, and the password was right there!

## Password For the Next Level

`[SPOILER]`

## What I Learned

* **Precision Searching**: I learned how to use the `find` command to filter files by very specific metadata.
* **The Power of '!'**: I learned that the exclamation mark can be used to negate conditions (find things that are *not* something).
* **Size Units**: In the `find` command, `c` is the suffix used for bytes, which is crucial for finding files with an exact size.

## Helpful Reading Material

* Mastering the search: [Find command examples](https://www.tecmint.com/35-practical-examples-of-linux-find-command/)
* Understanding file permissions: [Linux File Permissions Guide](https://www.redhat.com/en/blog/linux-file-permissions-explained)
