# Bandit28 -> 29: Git History Investigation

[Challenge](https://overthewire.org/wargames/bandit/bandit28.html)

## Level Description

There is a git repository at `ssh://bandit28-git@localhost/home/bandit28-git/repo`. The password for the next level is in there, but it seems someone has replaced the password with some "garbage" text in the current version of the file.

## The Process

This level teaches that **Git never forgets**. Even if the current version of a file looks wrong, the original data is likely still buried in the commit history.

### The Execution

1. **Clone the repo**: Just like the last level, I moved to `/tmp` and cloned the repository.
```bash
$ mkdir /tmp/git-hunt-28
$ cd /tmp/git-hunt-28
$ git clone ssh://bandit28-git@localhost:2220/home/bandit28-git/repo

```


2. **Check the current state**: I looked at `README.md`, but the password was obscured with `xxxxxxxx`.
3. **View the history**: I used `git log` to see a list of all changes (commits) made to this repository.
```bash
$ git log

```


I saw a commit message that said something like "fix: remove password from readme".
4. **Go back in time**: I needed to see what the file looked like *before* that "fix." I used `git show` to look at the previous commit, or I could use `git checkout` to jump back to that specific version.
```bash
$ git show HEAD^

```


*(The `^` symbol tells Git to show the version immediately before the current one.)*

The output showed the "diff" between the two versions. The lines starting with `-` were the ones removed—revealing the cleartext password before it was censored.

## Password For the Next Level

`[SPOILER]`

## What I Learned

* **Git Persistence**: I learned that "deleting" or "overwriting" sensitive data in a repository doesn't actually remove it from the history.
* **Git Log & Show**: I learned how to use `git log` to find the footprint of changes and `git show` to inspect the contents of specific commits.
* **Security Pitfalls**: This is a common real-world mistake where developers accidentally commit API keys or passwords and try to "fix" it by just deleting the line in a new commit.

## Helpful Reading Material

* Viewing history: [Git Log Documentation](https://git-scm.com/docs/git-log)
* Undoing/Viewing changes: [Git Basics - Undoing Things](https://git-scm.com/book/en/v2/Git-Basics-Undoing-Things)
