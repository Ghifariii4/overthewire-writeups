# Bandit19 -> 20: The SetUID Secret

[Challenge](https://overthewire.org/wargames/bandit/bandit19.html)

## Level Description

The password for the next level is stored in **/etc/bandit_pass/bandit20**. It can be accessed by using a **setuid binary** located in the home directory. You need to figure out how to use this binary to read the password file.

## The Process

When I logged in and looked around the home directory, I found an executable file named `bandit20-do`.

In Linux, a **SetUID (Set User ID)** file is a special type of executable. When run, it executes with the permissions of the file's **owner** rather than the person running it. In this case, `bandit20-do` is owned by **bandit20**. This means if I use this tool, I can act as bandit20 for a split second!

The name `bandit20-do` suggests it functions similarly to `sudo`. It "does" whatever command you tell it to do. To read the password, I simply told the binary to `cat` the protected file:

```bash
$ ./bandit20-do cat /etc/bandit_pass/bandit20

```

The binary executed the `cat` command with bandit20's permissions, bypassed the usual restriction, and displayed the password.

## Password For the Next Level

`[SPOILER]`

## What I Learned

* **SetUID Binaries**: I learned that certain files have a "special" permission (often indicated by an `s` in the file permissions like `-rwsr-xr-x`) that allows them to run as the owner.
* **Privilege Escalation**: This is a classic example of how certain tools are designed to allow lower-privilege users to perform specific high-privilege tasks safely.
* **Effective User IDs**: I learned that your "identity" on a Linux system can temporarily change depending on the tools you are using.

## Helpful Reading Material

* Understanding special permissions: [SetUID, SetGID, and Sticky Bit Explained](https://www.google.com/search?q=https://www.geeksforgeeks.org/setuid-setgid-and-sticky-bit-in-linux-file-permissions/)
* Linux Permissions: [The chmod and sbit guide](https://www.google.com/search?q=https://linuxconfig.org/how-to-use-special-permissions-setuid-setgid-and-sticky-bit)
