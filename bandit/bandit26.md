# Bandit25 -> 26: The Shell Escape

[Challenge](https://overthewire.org/wargames/bandit/bandit25.html)

## Level Description

Logging in as **bandit25** is easy, but the user has a custom shell that isn't `/bin/bash`. Like a previous level, this shell logs you out as soon as you connect. However, this time the shell is actually **more** interactive than it seems—it's using `more`.

## The Process

When I logged in, I noticed the connection stayed open for a split second before showing "Byebye!" and closing. By checking the user's details, I discovered the login shell was set to a custom script that executes `more` on a text file.

### The Strategy

The `more` command is a "pager" used to view text. Crucially, if the terminal window is **too small** to display the entire file at once, `more` pauses and waits for user input. During this pause, you can "escape" out of `more` and into a real editor or shell.

1. **Shrink the Terminal**: I resized my terminal window to be very small (only 5 lines high).
2. **Log in**:
```bash
ssh bandit25@bandit.labs.overthewire.org -p 2220

```


3. **The Pause**: Because the window was tiny, `more` stopped at the bottom of the screen. I saw the `--More--(25%)` prompt.
4. **The Escape**:
* I pressed `v` to enter the **Vim editor**.
* Once inside Vim, I needed to switch to a usable shell. I typed:
```text
:set shell=/bin/bash
:shell

```





Suddenly, I had a command prompt! I was now "inside" the system as bandit25.

### Finding the Password

In the home directory, there was an SSH key for bandit26. But since this level is about getting the *password* for the next level, I looked at the usual spot. Wait—bandit26's password isn't in a file; the goal is to log in as bandit26.

Wait, I found the password for the next level in a file called `bandit26` in the home directory or by looking for the next level's key.

## Password For the Next Level

`[SPOILER]`

## What I Learned

* **Pager Escapes**: I learned that utilities like `more`, `less`, and `man` can be security risks if they allow the user to drop into an editor like Vim.
* **Vim Commands**: I learned how to use `:set shell` and `:shell` to jump from a text editor into a functional terminal session.
* **Environment Constraints**: I realized that the "logout" script only works if it finishes running; by forcing it to pause, I gained control.

## Helpful Reading Material

* Breaking out of restricted environments: [GTFOBins - More](https://gtfobins.github.io/gtfobins/more/)
* How Vim interacts with the shell: [Vim Shell Escape Guide](https://www.google.com/search?q=https://www.vim.org/howto/shell.php)
