# Bandit32 -> 33: The Uppercase Shell (Uppershell)

[Challenge](https://overthewire.org/wargames/bandit/bandit32.html)

## Level Description

After logging in as **bandit32**, you find yourself in a very strange shell. It’s not Bash, and it’s not `more`. This shell seems to convert everything you type into **UPPERCASE**. If you try to run commands like `ls` or `cd`, the shell sees `LS` and `CD`, which aren't valid Linux commands.

## The Process

This is a classic "Restricted Shell" escape. The shell is a simple script that takes user input, transforms it to uppercase using something like `tr '[:lower:]' '[:upper:]'`, and then tries to execute it.

Since Linux commands are **case-sensitive**, `ls` works but `LS` fails. I needed to find a way to execute a command that doesn't rely on lowercase letters or find a way to "break" the shell's logic.

### The Strategy

In many shell environments, there are special variables or "shorthands" that represent the shell itself. One of the most famous is `$0`.

In a script or shell:

* `$1`, `$2`, etc., are arguments.
* **`$0`** represents the name of the shell or the script currently running.

When I typed `$0` into the Uppershell, the following happened:

1. The shell saw `$0`.
2. Because `$0` is a variable, the shell evaluated it *before* trying to uppercase the literal string (or the evaluation itself bypassed the filter).
3. `$0` evaluated to the current execution context, which in this case, dropped me back into a standard, functional `/bin/sh`.

### The Execution

```text
>> $0
$ 

```

Suddenly, the `>>` prompt disappeared and was replaced by a simple `$`. I was now in a normal shell. I could then grab the password for the final level:

```bash
$ cat /etc/bandit_pass/bandit33

```

## Password For the Next Level

`[SPOILER]`

## What I Learned

* **Positional Parameters**: I learned that `$0` is a powerful variable that can be used to call the current shell or script execution environment.
* **Case Sensitivity**: I reinforced my understanding that `WHOAMI` is not the same as `whoami` in the Linux world.
* **Shell Escapes**: This was a creative look at how simple input filters can be bypassed by using shell variables that evaluate to system paths.

## Helpful Reading Material

* Special Shell Variables: [Bash Variables Cheat Sheet](https://www.google.com/search?q=https://devhints.io/bash%23special-parameters)
* Case Sensitivity in Linux: [Why Linux is Case Sensitive](https://www.google.com/search?q=https://www.howtogeek.com/198358/ask-htg-why-is-linux-case-sensitive-and-windows-isnt/)
