# Bandit31 -> 32: Pushing to the Repository

[Challenge](https://overthewire.org/wargames/bandit/bandit31.html)

## Level Description

There is a git repository at `ssh://bandit31-git@localhost/home/bandit31-git/repo`. This time, you don't just need to find something—you need to **push a file** to the remote repository to get the password back as a response.

## The Process

In previous levels, we only pulled data *down*. In this level, we use the "Push" side of Git. The server's `post-receive` hook (a script that runs after you upload code) is configured to check if you uploaded a specific file and, if so, give you the password.

### The Execution

1. **Clone the repo**:
```bash
$ mkdir /tmp/push-test
$ cd /tmp/push-test
$ git clone ssh://bandit31-git@localhost:2220/home/bandit27-git/repo

```


2. **Read the instructions**:
I checked the `README.md` in the repo. it said:
> "To get the password, create a file named **key.txt** with the content **'May I have the password please?'** and push it to the master branch."


3. **Create the file**:
```bash
$ echo "May I have the password please?" > key.txt

```


4. **Add and Commit**:
Git doesn't automatically track new files. I had to "stage" it and then "commit" it to the local history.
```bash
$ git add key.txt
$ git commit -m "Providing the key"

```


*Note: If it asks for your email/name, just run the suggested `git config` commands with fake info.*
5. **The Push**:
Now, I sent the changes back to the server:
```bash
$ git push origin master

```



As soon as the push finished, the server's output printed a long message. Embedded in that text was the password for Bandit32!

## Password For the Next Level

`[SPOILER]`

## What I Learned

* **Git Push**: I learned how to send local changes to a remote server.
* **Server-Side Hooks**: I learned that Git servers can be programmed to perform actions (like giving out passwords) whenever a user pushes code.
* **Staging vs. Committing**: I practiced the three-step workflow: **Add** (stage), **Commit** (save locally), and **Push** (upload).

## Helpful Reading Material

* Contributing to a repo: [Git Add, Commit, Push Guide](https://www.atlassian.com/git/tutorials/saving-changes)
* Git Hooks: [An introduction to Git Hooks](https://githooks.com/)
