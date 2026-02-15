# Bandit01 -> 02: Simply lovely Dash

[Challenge](https://overthewire.org/wargames/bandit/bandit2.html)

## Level Description

The instruction for this level is quite clear tho, they said the password for the next level is stroed in a file called `-`, and its located in the home directory. So, let's go.

## The Process

Just like the previous level, I check the home directory first with `ls` and there is a file named `-`.

I little bit confused, and then I remember that we can use command `cat` with addon `<` for read a filename with dash.

I type

```bash
$ cat < -
```

There  it is, the password for the next level.

## Password for the Next Level

`[SPOILER]`

## What I Learned

- **Handling Special Filenames**: Files named with special characters like `-` can confuse commands. Give the add phrase like `<` for open file with Dash name.
- **Clearing Command Usage Confusion**: When a command doesn’t behave as expected, look closely at the error or usage messages—they can point you toward the solution.
- **Reinforcing File Operations**: Commands like `cat` can have quirks, and understanding how to handle them is key for CTF challenges.

## Helpful Reading Material

- `man cat` – The manual page can help you understand why `-` is treated as a special option.
- [Linux Handling Special Filenames](https://medium.com/@.Qubit/how-to-create-open-find-remove-dashed-filename-in-linux-27ee297d1740)