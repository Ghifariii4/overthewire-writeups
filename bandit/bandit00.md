# bandit00: Log Into Remote Server

[Challenge](https://overthewire.org/wargames/bandit/bandit0.html)

---

## Level Description

This was the starting  point of the bandit wargame. The goal of this level is for you to log into the game using SSH. The host to which you need to connect is <a href="[URL-Tujuan](https://overthewire.org/wargames/bandit)">bandit.labs.overthewire.org</a>, on port *2220*. The username is bandit0 and the password is bandit0. Once logged in, go to the Level 1 page to find out how to beat Level 1.

## The Process

So I was ready at my terminal, the Instruction were clear: I need to use SSH, but there was a custom port that is `2229`. SSH, by default, connects on port `22`, so I use that custom port to connect to bandit server.

Here's how I did it:

```bash
$ ssh bandit0@bandit.labs.ooverthewire.org -p 2220
```

When asked for password, I entered `[SPOILER]`

Yeah, I just hop into the Bandit's server, which mean I had succesfully logged in. YEAYY. this is just a beginning XD

## Password For the Next Level

`[SPOILER]`

## what I learned

- **Using SSH:** I got hands-on experience connecting to a remote server.
- **Specifying Ports:** By default, SSH uses port 22, but for this challenge, I learned how to connect to a custom port with the `-p` flag.
- **Basic Authentication:** It’s always good to know how to log in with just a username and password.


## Helpful Reading Material

- Always check out `man ssh` on your terminal—It’s like having the SSH manual right there in your pocket.
- If you’re new to SSH, check out this guide: [OpenSSH Server Documentation](https://ubuntu.com/server/docs/openssh-server)

