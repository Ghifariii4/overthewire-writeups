# Bandit27 -> 28: Exploring the Git Repository

[Challenge](https://overthewire.org/wargames/bandit/bandit27.html)

## Level Description

The password for the next level is stored in a **Git repository** at `ssh://bandit27-git@localhost/home/bandit27-git/repo`. You need to clone this repository to find the password.

## The Process

This level introduces **Git**, the most popular version control system in the world. Instead of searching a file system, I had to download (clone) a project history.

Since I couldn't write to the current directory, I created a temporary workspace in `/tmp`, cloned the repository, and then looked at the contents.

### The Execution

1. **Create a temporary directory**:
```bash
$ mkdir /tmp/myclonedrepo
$ cd /tmp/myclonedrepo

```


2. **Clone the repository**:
I used the `git clone` command. The server asked for the password for `bandit27-git` (which is the same as the password for the current level, `bandit27`).
```bash
$ git clone ssh://bandit27-git@localhost:2220/home/bandit27-git/repo

```


3. **Inspect the files**:
Once cloned, a new directory named `repo` appeared. I entered it and listed the files.
```bash
$ cd repo
$ ls
$ cat README

```



The password was sitting right there inside the `README` file.

## Password For the Next Level

`[SPOILER]`

## What I Learned

* **Git Basics**: I learned how to use `git clone` to retrieve a copy of a remote repository.
* **Remote URLs**: I practiced using SSH-based URLs to access private repositories.
* **Temporary Workspaces**: I reinforced the habit of using `/tmp` when I don't have write permissions in my home directory.

## Helpful Reading Material

* Getting started with Git: [Git Clone Documentation](https://git-scm.com/docs/git-clone)
* What is Git?: [The Beginner's Guide to Git](https://www.atlassian.com/git/tutorials/what-is-version-control)
