# Bandit10 -> 11: Base64 Decoding

[Challenge](https://overthewire.org/wargames/bandit/bandit10.html)

## Level Description

The password for the next level is stored in the file **data.txt**, which contains **Base64** encoded data. Base64 is a way of representing binary data in an ASCII string format, often used in emails or web applications.

## The Process

When I opened `data.txt`, I saw a long string of characters ending with an equals sign `=`, which is a classic indicator of Base64 encoding. It isn't encrypted, just "translated" into a different format.

To get the password, I needed to decode it back into a human-readable string. Linux has a built-in tool called `base64` that can handle this perfectly.

Here is the command I used:

```bash
$ base64 -d data.txt

```

The `-d` flag stands for **decode**. As soon as I ran it, the encoded block disappeared, and the plain text password for the next level was revealed.

## Password For the Next Level

`[SPOILER]`

## What I Learned

* **Encoding vs. Encryption**: I learned that Base64 is an encoding method, not encryption. Anyone with the right tool can decode it instantly.
* **Base64 Indicators**: I learned to recognize Base64 strings by their look (a mix of upper/lower case letters, numbers, and padding symbols like `==`).
* **The base64 Tool**: I learned how to use the command line to both encode and decode data on the fly.

## Helpful Reading Material

* What is Base64?: [Base64 Encoding Explained](https://developer.mozilla.org/en-US/docs/Glossary/Base64)
* Command usage: [Linux base64 Command Examples](https://www.google.com/search?q=https://www.geeksforgeeks.org/base64-command-in-linux-with-examples/)
