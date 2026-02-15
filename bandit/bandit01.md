# bandit00 -> 01: list

[Challenge](https://overthewire.org/wargames/bandit/bandit1.html)

## Level Description

The goal of this level was very clear, they said that the password for the next level is stored in a file called readme located in the home directory. Once I found it, I logged in to next level use SSH on port `2220`

## The Process

So as the instruction said the password stored in file name readme, I check first the home directory.

I type `ls` in home directory and there it is, file readme. Next I wanna check contents of the file.

I used the `cat` command to see inside the file.

```bash
$ cat readme
```

And there it was, the password for next level.

## Password for the next level

`[REDACTED]`

## What I learned

- **File listing (`ls`)**: Always check your surroundings first! The `ls` command is your best friend for seeing what files are available.
- **Reading Files (`cat`)**: Simple yet powerful, `cat` allows you to quickly view the contents of a file.
- **Logging into Next Levels**: Every password is used to log into the next level using SSH, reinforcing how to string together progress in a sequence.
