# Bandit13 -> 14: Private Key SSH

[Challenge](https://overthewire.org/wargames/bandit/bandit13.html)

## Level Description

The password for the next level is stored in **/etc/bandit_pass/bandit14** and can only be read by user **bandit14**. For this level, you don't get the next password, but you get a **private SSH key** that can be used to log into the next level.

## The Process

Logging in, I didn't see a `data.txt` file this time. Instead, there was a file named `sshkey.private`. This is an RSA private key. In Linux security, you can often log into a server using a "key pair" (a public key and a private key) instead of a traditional password.

Since the goal was to log into `bandit14` on the same machine, I used the `ssh` command and pointed it to this private key using the `-i` (identity) flag.

Here is how I did it:

```bash
$ ssh -i sshkey.private bandit14@localhost -p 2220

```

Once I hit enter, the server accepted the key, and I was logged in as `bandit14` without ever typing a password! From there, I simply went to the "sacred" directory where Bandit passwords are kept:

```bash
$ cat /etc/bandit_pass/bandit14

```

The password for level 15 appeared instantly.

## Password For the Next Level

`[SPOILER]`

## What I Learned

* **SSH Identities**: I learned that the `-i` flag is used to provide a private key for authentication.
* **Localhost**: I learned that `localhost` (or `127.0.0.1`) refers to the machine you are currently working on.
* **Key-Based Auth**: I realized that using keys is much more secure than passwords, as long as you keep your private key safe!

## Helpful Reading Material

* How SSH keys work: [SSH Key Authentication Explained](https://www.digitalocean.com/community/tutorials/ssh-essentials-working-with-ssh-servers-clients-and-keys)
* SSH Command Flags: [SSH Command Manual](https://linux.die.net/man/1/ssh)
