# Bandit11 -> 12: The ROT13 Scramble

[Challenge](https://overthewire.org/wargames/bandit/bandit11.html)

## Level Description

The password for the next level is stored in **data.txt**, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions. This is a classic substitution cipher known as **ROT13**.

## The Process

When I looked at `data.txt`, the text looked like complete gibberish. However, knowing it was ROT13 made it a fun puzzle to solve. ROT13 works by replacing a letter with the 13th letter after it in the alphabet. Since there are 26 letters in the English alphabet, applying ROT13 twice gets you back to the original text!

To "unscramble" this, I used the `tr` (translate) command. This tool allows you to map one set of characters to another. I mapped the standard alphabet to an alphabet starting 13 letters in.

Here is the command I used:

```bash
$ cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'

```

Breakdown of the command:

* `tr 'A-Za-z'`: This defines the input set (the normal alphabet).
* `'N-ZA-Mn-za-m'`: This defines the output set. It starts at 'N' (the 13th letter) and wraps back around to 'M'.

The result was a perfectly readable password. Caesar would be proud!

## Password For the Next Level

`[SPOILER]`

## What I Learned

* **Simple Ciphers**: I learned about ROT13, one of the oldest and simplest forms of character substitution.
* **The 'tr' Command**: I discovered how powerful the `tr` tool is for mapping and transforming text strings on the fly.
* **Alphabet Mapping**: I learned how to define ranges in the command line to manipulate text programmatically.

## Helpful Reading Material

* The history of ROT13: [ROT13 - Wikipedia](https://en.wikipedia.org/wiki/ROT13)
* Mastering character translation: [Linux tr Command Examples](https://www.google.com/search?q=https://www.tecmint.com/linux-tr-command-examples/)
