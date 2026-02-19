# Bandit12 -> 13: The Matryoshka Doll

[Challenge](https://overthewire.org/wargames/bandit/bandit12.html)

## Level Description

The password for the next level is stored in the file **data.txt**, which is a hexdump of a file that has been repeatedly compressed. For this level, it’s helpful to create a directory under `/tmp` in which you can work.

## The Process

This level was like playing with a Russian nesting doll (Matryoshka). The file wasn't just compressed; it was a **hexdump** that I first had to convert back to binary, and then I had to peel back multiple layers of different types of compression.

First, I created a workspace in `/tmp` and copied the file there. Then, I used `xxd` to reverse the hexdump:

```bash
$ mkdir /tmp/mywork
$ cp data.txt /tmp/mywork
$ cd /tmp/mywork
$ xxd -r data.txt > data.bin

```

From here, it was a repetitive cycle of identifying the file type and decompressing it:

1. **Check file type**: I used `file data.bin` to see what kind of compression was used (gzip, bzip2, or tar).
2. **Decompress**: Based on the type, I used `gunzip`, `bunzip2`, or `tar -xf`.
3. **Repeat**: I kept doing this until `file` finally reported "ASCII text."

After about 8 or 9 layers of "sialan" (as I called it in my notes!), I finally reached the end and read the file with `cat`.

## Password For the Next Level

`[SPOILER]`

## What I Learned

* **Hexdump Reversal**: I learned how to use `xxd -r` to turn a text-based hex representation back into a functional binary file.
* **The Importance of 'file'**: Since the filenames didn't have extensions, the `file` command was the only way to know which decompression tool to use.
* **Persistence**: Some challenges require doing the same technical steps repeatedly until you reach the core data.

## Helpful Reading Material

* Identify any file: [The Linux File Command](https://linux.die.net/man/1/file)
* Working with Hex: [Using the xxd command](https://www.google.com/search?q=https://www.geeksforgeeks.org/xxd-command-in-linux-with-examples/)
