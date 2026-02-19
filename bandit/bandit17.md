# Bandit16 -> 17: Port Scanning and SSL

[Challenge](https://overthewire.org/wargames/bandit/bandit16.html)

## Level Description

The password for the next level can be retrieved by submitting the password of the current level to a port on **localhost** in the range **31000 to 32000**. First, you need to find out which ports are listening and which of them "speak" SSL. Only one will give you the password, while others will simply echo back what you send.

## The Process

This level was a bit more complex. Instead of being told exactly where to go, I had to "scout" the network first. I used **Nmap**, a famous network scanning tool, to find open ports in the specified range.

I ran this command to see which ports were open and what services they were running:

```bash
$ nmap -p 31000-32000 localhost

```

The scan showed several open ports. To find the one that gives the password, I had to test the SSL ports. I used `openssl s_client` (just like in Level 15) to connect to them.

When I connected to the correct port and sent the `bandit16` password, the server didn't just give me a string—it gave me an **RSA Private Key**.

I copied this key, saved it to a file in `/tmp`, and changed its permissions (SSH keys won't work if they are "too world-readable"):

```bash
$ nano /tmp/bandit17_key
$ chmod 600 /tmp/bandit17_key
$ ssh -i /tmp/bandit17_key bandit17@localhost -p 2220

```

Once logged in as `bandit17`, I could easily grab the password from the usual location.

## Password For the Next Level

`[SPOILER]`

## What I Learned

* **Port Scanning**: I learned how to use `nmap` to discover active services on a network range.
* **Service Discrimination**: I learned that even if multiple ports are open, they might behave differently (echo vs. providing data).
* **SSH Key Permissions**: I learned that private keys must have restricted permissions (`chmod 600`) for the SSH client to accept them.

## Helpful Reading Material

* Nmap basics: [Nmap Reference Guide](https://nmap.org/book/man.html)
* Secure File Permissions: [Understanding Chmod 600](https://www.computerhope.com/unix/uchmod.htm)
