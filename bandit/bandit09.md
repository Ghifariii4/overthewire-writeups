# Bandit08 -> 09: The Only Unique One

[Challenge](https://overthewire.org/wargames/bandit/bandit8.html)

## Level Description

The password for the next level is stored in the file **data.txt** and is the only line of text that occurs **only once**. The file is full of repeated lines, so we need to filter them out!

## The Process

Logging in, I found another `data.txt` file. This time, the challenge wasn't finding a keyword, but finding a unique needle in a sea of duplicates.

I used two powerful commands together: `sort` and `uniq`. Here is the catch: the `uniq` command only works correctly on text that is already sorted, because it compares a line to the one immediately following it.

Here is the pipeline I used:

```bash
$ sort data.txt | uniq -u

```

Here is why this worked:

* `sort data.txt`: This organized the file alphabetically, putting all identical lines right next to each other.
* `|`: The pipe took the sorted list and passed it to the next command.
* `uniq -u`: The `-u` flag stands for "unique." It tells the command to *only* display lines that are not repeated at all.

The terminal blinked and spit out exactly one line. That was our password!

## Password For the Next Level

`[SPOILER]`

## What I Learned

* **Piping Commands**: I learned how to "chain" commands together using `|` to solve complex problems step-by-step.
* **The Sort-Uniq Combo**: This is a classic Linux trick. Remember: always `sort` before you `uniq`!
* **Filtering Output**: I learned that flags like `-u` can change the behavior of a tool to give me exactly the data I need.

## Helpful Reading Material

* Handling duplicate lines: [The Linux uniq Command](https://www.geeksforgeeks.org/uniq-command-in-linux-with-examples/)
* Sorting data: [Sort Command in Linux](https://www.google.com/search?q=https://linuxize.com/post/sort-command-in-linux/)
