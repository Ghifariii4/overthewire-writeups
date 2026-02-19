# Bandit30 -> 31: The Hidden Tag

[Challenge](https://overthewire.org/wargames/bandit/bandit30.html)

## Level Description

There is a git repository at `ssh://bandit30-git@localhost/home/bandit30-git/repo`. The password for the next level is in there, but it isn't in the files, the history, or the branches.

## The Process

If a secret isn't in a branch or the standard log, it might be attached to a **Tag**. In Git, tags are used to mark specific points in history as being important (like a version release: `v1.0`, `v2.0`).

### The Execution

1. **Clone the repo**:
```bash
$ mkdir /tmp/tag-hunt
$ cd /tmp/tag-hunt
$ git clone ssh://bandit30-git@localhost:2220/home/bandit30-git/repo

```


2. **Search everything**:
I checked `git branch -a` and `git log`, but they looked empty or unhelpful.
3. **Check for tags**:
I used the `tag` command to see if any labels had been created:
```bash
$ git tag

```


The output showed a tag named `secret`.
4. **Inspect the tag**:
A tag is just a pointer to a commit. I used `git show` to see what that specific tag contained:
```bash
$ git show secret

```



The `git show` command revealed the content associated with that tag, which was the password for the next level.

## Password For the Next Level

`[SPOILER]`

## What I Learned

* **Git Tags**: I learned that tags are a different way to reference commits and are often overlooked during a basic search.
* **Git Show Universality**: I realized that `git show` works on almost any Git object—commits, branches, and tags alike.
* **Hidden Metadata**: This level reinforced the idea that in version control, data can be "hidden" in metadata labels rather than in the files themselves.

## Helpful Reading Material

* Labeling history: [Git Basics - Tagging](https://git-scm.com/book/en/v2/Git-Basics-Tagging)
* Inspecting tags: [How to use git show for tags](https://www.google.com/search?q=https://linuxize.com/post/git-show-command/)
