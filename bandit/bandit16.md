# Bandit15 -> 16: Encrypted Communication (SSL)

[Challenge](https://overthewire.org/wargames/bandit/bandit15.html)

## Level Description

The password for the next level can be retrieved by submitting the password of the current level to **port 30001 on localhost using SSL encryption**.

## The Process

This level is very similar to the last one, but with a twist: the service on port 30001 requires an **SSL/TLS encrypted connection**. If I try to use regular Netcat (`nc`), the connection will fail because Netcat doesn't know how to "speak" in encryption.

To solve this, I used `openssl`, a toolkit for the Transport Layer Security (TLS) and Secure Sockets Layer (SSL) protocols. I used the `s_client` tool to initiate a secure connection.

Here is the command I used:

```bash
$ openssl s_client -connect localhost:30001

```

Once the connection was established and the "handshake" was finished, the terminal waited for my input. I pasted the password for `bandit15`, and the server responded with the password for Level 16.

## Password For the Next Level

`[SPOILER]`

## What I Learned

* **SSL/TLS vs. Plaintext**: I learned that some services require encrypted connections to protect the data being sent over the network.
* **OpenSSL s_client**: I learned how to use this tool as an alternative to Netcat for interacting with secure network services.
* **Secure Handshakes**: I saw how the client and server negotiate a secure connection before any real data (like the password) is exchanged.

## Helpful Reading Material

* Secure connections: [OpenSSL s_client Documentation](https://www.openssl.org/docs/man1.1.1/man1/s_client.html)
* Encryption basics: [What is SSL, TLS, and HTTPS?](https://www.google.com/search?q=https://www.digicert.com/blog/what-is-ssl-tls-and-https)
