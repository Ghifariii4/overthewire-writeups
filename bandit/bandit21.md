# Bandit20 -> 21: Connecting to Yourself

[Challenge](https://overthewire.org/wargames/bandit/bandit20.html)

## Level Description

There is another **setuid binary** in the home directory called `suconnect`. This one works by connecting to a port on **localhost** that you specify as an argument. It will then read a line of text from the connection and compare it to the password in the current level (`bandit20`). If they match, it will transmit the password for the next level (`bandit21`).

## The Process

This level required me to be in two places at once: I needed to **listen** for a connection and **send** the password, while simultaneously running the `suconnect` binary to **connect** to that listener.

To do this, I used two terminal sessions or used the background process trick:

1. **Start a listener**: I used Netcat to listen on a random port (let's say 1234). I used the `-l` (listen) flag and prepared it to send the current password.
```bash
$ echo "PASSWORD_FROM_BANDIT20" | nc -l -p 1234 &

```


*Note: The `&` at the end puts the listener in the background so I can keep using the same terminal.*
2. **Run the binary**: I then ran the `suconnect` tool and told it to connect to my waiting listener on that same port.
```bash
$ ./suconnect 1234

```



The binary connected to my Netcat listener, received the password I "piped" into it, verified it was correct, and then printed the password for `bandit21`.

## Password For the Next Level

`[SPOILER]`

## What I Learned

* **Network Handshakes**: I learned how a program can verify credentials by communicating over a local network socket.
* **Background Processes**: I learned that using `&` allows me to run a service (like a listener) while I continue to execute other commands.
* **Inter-Process Communication**: This challenge showed how two different programs (Netcat and `suconnect`) can talk to each other to exchange secrets.

## Helpful Reading Material

* Backgrounding jobs: [Bash Job Control Basics](https://www.google.com/search?q=https://www.digitalocean.com/community/tutorials/how-to-use-bash-job-control-on-linux)
* Netcat listening: [Using Netcat as a simple server](https://www.google.com/search?q=https://opensource.com/article/20/8/netcat)
