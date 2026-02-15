# Bandit02 -> 03: Look at the spaces

[Challenge](https://overthewire.org/wargames/bandit/bandit3.html)

## Level Description

Start with the clue that said, the password for the next level is stored in file called `--spaces in this filename-- ` and its located in home directory. I think this level quite same like the previous, there is a file with dash name and there is a space between it.

## The Process

The first thing I did is check the home directory with command:

```bash
$ ls
```

And then I found the file named `--spaces in this filename--`. Just like Level 02, I use command `cat` with some input redirection `<` and apostrophe `(``)` to manipulate the spacing:

```bash
$ cat < '--spaces in this filename--'
```
Yup, There it is, password for the next level.

## Password for the Next Level

`[SPOILER]`

## What I Learned

- **Combining Challenges**: Handling files that contain both dashes and spaces requires a combination of techniques.

- **The Power of Redirection**: Using `<` is a powerful *“trick”* to avoid Common Options errors. Because the file is opened by Shell before the command is executed, the cat program will not attempt to read `--` as a system parameter.

- **Quoting Special Characters**: Single quotes `(')` ensure that the entire sequence of words and symbols within them is considered a single file name.
