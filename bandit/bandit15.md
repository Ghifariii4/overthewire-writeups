# Bandit14 -> 15: The Netcat Handshake

[Challenge](https://overthewire.org/wargames/bandit/bandit14.html)

## Level Description

The password for the next level can be retrieved by submitting the password of the current level to **port 30000 on localhost**.

## The Process

In this level, the password isn't hidden in a file or a git repo—it's behind a network service. I already had the password for `bandit14` (which I found in the previous level at `/etc/bandit_pass/bandit14`). Now, I needed to "talk" to the server on a specific port to get the next one.

I used **Netcat** (`nc`), which is often called the "Swiss Army Knife" of networking. It allows you to open TCP/UDP connections and send data directly.

Here is how I sent the password to the service:

```bash
$ cat /etc/bandit_pass/bandit14 | nc localhost 30000

```

By using the pipe `|`, I sent the content of the password file directly into the Netcat connection. The server received the password, verified it, and immediately replied with the password for Level 15.

## Password For the Next Level

`[SPOILER]`

## What I Learned

* **Netcat Basics**: I learned how to use `nc` to connect to a specific port on a server.
* **Localhost Communication**: I practiced interacting with services running on the same machine I am logged into.
* **Network Interaction**: I learned that some passwords or secrets are only revealed when you provide the correct "handshake" to a network service.

## Helpful Reading Material

* The power of Netcat: [Netcat (nc) Command with Examples](https://linuxize.com/post/netcat-nc-command-with-examples/)
* Understanding Ports: [What is a Computer Port?](https://www.cloudflare.com/learning/network-layer/what-is-a-computer-port/)
