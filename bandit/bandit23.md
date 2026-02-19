# Bandit22 -> 23: Dynamic Filenames in Cron

[Challenge](https://overthewire.org/wargames/bandit/bandit22.html)

## Level Description

A program is running periodically from **cron**. Check **/etc/cron.d/** for the configuration and see what command is being executed. This time, the script uses a more complex way to name the output file.

## The Process

Similar to the last level, I checked the cron configuration:

```bash
$ cat /etc/cron.d/cronjob_bandit23

```

This led me to a script: `/usr/bin/cronjob_bandit23.sh`. When I looked at the contents of that script, things got interesting:

```bash
#!/bin/bash

myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

cat /etc/bandit_pass/$myname > /tmp/$mytarget

```

### The Logic

The script doesn't use a fixed filename. Instead, it calculates a **hash** (a unique fingerprint) based on the username.

1. It takes the string `"I am user bandit23"`.
2. It passes that string through `md5sum` to create a hash.
3. It uses that hash as the filename in `/tmp`.

To find the password, I had to replicate that calculation myself for the user **bandit23** to figure out where the script hid the file:

```bash
$ echo I am user bandit23 | md5sum | cut -d ' ' -f 1

```

This gave me a specific hexadecimal string (the hash). I then simply `cat`ed that file from the `/tmp` directory:

```bash
$ cat /tmp/[THE_HASH_I_FOUND]

```

## Password For the Next Level

`[SPOILER]`

## What I Learned

* **Predictable Secret Filenames**: I learned that even if a filename is "random-looking" (like a hash), if the logic used to create it is known, it can be predicted.
* **MD5 Hashing**: I learned how to generate an MD5 hash from a string using the command line.
* **Variable Substitution**: I saw how shell scripts use variables like `$myname` to perform actions dynamically.

## Helpful Reading Material

* Hashing on the CLI: [How to use md5sum](https://www.google.com/search?q=https://www.geeksforgeeks.org/md5sum-command-in-linux-with-examples/)
* String manipulation: [Using 'cut' to format output](https://linuxize.com/post/linux-cut-command/)
