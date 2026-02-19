# Bandit18 -> 19: The Finicky Shell

[Challenge](https://overthewire.org/wargames/bandit/bandit18.html)

## Level Description

The password for the next level is stored in a file called **readme** in the home directory. However, there is a catch: someone has modified the `.bashrc` (or login profile) of the **bandit18** user to log you out immediately upon login.

## The Process

When I tried to log in normally using `ssh bandit18@bandit.labs.overthewire.org`, I saw a "Byebye!" message, and the connection closed instantly. This is a common trick where a script is set to run at login that terminates the session.

To bypass this, I needed to tell SSH to execute a specific command *instead* of starting the default interactive shell. By providing a command at the end of my SSH string, the server runs that command and then closes, bypassing the "logout" script in the profile.

Here is the command I used from my local terminal:

```bash
$ ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme

```

By adding `cat readme` at the end, I told the server: "Don't worry about giving me a prompt; just read that file and send the text back to me." It worked perfectly, and the password was printed directly to my screen.

## Password For the Next Level

`[SPOILER]`

## What I Learned

* **Remote Command Execution**: I learned that SSH isn't just for interactive shells; you can use it to run single commands on a remote server.
* **Bypassing Login Scripts**: I learned that `.bashrc` and `.profile` files only affect interactive sessions, and providing a command directly can often bypass restrictions placed within them.
* **Non-Interactive SSH**: This is a vital skill for automation and scripting where you need to fetch data from a server without "logging in" manually.

## Helpful Reading Material

* Running remote commands: [SSH Command Execution](https://www.ssh.com/academy/ssh/command)
* Understanding login scripts: [The difference between .bashrc and .bash_profile](https://www.google.com/search?q=https://blog.flowblok.com/2013/02/05/shell-startup-scripts.html)
