# Bandit29 -> 30: Secrets in the Branch

[Challenge](https://overthewire.org/wargames/bandit/bandit29.html)

## Level Description

There is a git repository at `ssh://bandit29-git@localhost/home/bandit29-git/repo`. The password for the next level is in there, but it is not in the "master" (main) branch.

## The Process

In Git, **branches** are like parallel universes. Developers use them to work on new features without messing up the main code. If you can't find a secret in the main branch, it might be hidden in another one.

### The Execution

1. **Clone the repo**:
```bash
$ mkdir /tmp/branch-hunt
$ cd /tmp/branch-hunt
$ git clone ssh://bandit29-git@localhost:2220/home/bandit29-git/repo

```


2. **Look for other branches**:
Standard `git branch` only shows local branches. To see everything available on the server, I used the `-a` (all) flag:
```bash
$ git branch -a

```


I noticed a branch named `remotes/origin/dev`.
3. **Switch branches**:
I "checked out" the development branch to see what was inside:
```bash
$ git checkout dev

```


4. **Find the password**:
Now that I was in the `dev` universe, I checked the files again:
```bash
$ ls
$ cat README.md

```



The `README.md` on the `dev` branch contained the password, whereas the master branch version claimed there were no passwords.

## Password For the Next Level

`[SPOILER]`

## What I Learned

* **Git Branches**: I learned that a repository can hold multiple versions of a project simultaneously.
* **Remote Branches**: I learned that `git branch -a` is necessary to see branches that exist on the server but haven't been downloaded locally yet.
* **Context Switching**: I practiced using `git checkout` to move between different states of the project.

## Helpful Reading Material

* Branching Basics: [Git Branching - What a Branch Is](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)
* Switching branches: [Git Checkout Guide](https://www.atlassian.com/git/tutorials/using-branches/git-checkout)
