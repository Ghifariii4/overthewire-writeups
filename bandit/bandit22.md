# Bandit21 -> 22: The Scheduled Task (Cron)

[Challenge](https://overthewire.org/wargames/bandit/bandit21.html)

## Level Description

A program is running periodically at regular intervals from **cron**, the system-wide job scheduler. Look in **/etc/cron.d/** for the configuration and see what command is being executed.

## The Process

In Linux, `cron` is like an alarm clock that triggers scripts or commands at specific times. To solve this, I needed to investigate how the system was automated.

I started by looking into the cron configuration directory to find a job related to bandit22:

```bash
$ ls /etc/cron.d/
$ cat /etc/cron.d/cronjob_bandit22

```

The output showed a line indicating that every minute, a shell script was being executed as user `bandit22`:
`@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null`
`* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null`

Next, I read the script to see what it actually does:

```bash
$ cat /usr/bin/cronjob_bandit22.sh

```

The script was very simple:

```bash
#!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZSc7sg2
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZSc7sg2

```

The script copies the password for `bandit22` into a world-readable file in the `/tmp` directory. I just had to `cat` that temporary file to get the prize!

```bash
$ cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZSc7sg2

```

## Password For the Next Level

`[SPOILER]`

## What I Learned

* **Cron Jobs**: I learned that `/etc/cron.d/` contains files that define scheduled tasks for the whole system.
* **Script Analysis**: I practiced reading shell scripts to understand how data is moved or transformed by automated processes.
* **Permissions in /tmp**: I saw how temporary directories are often used by scripts to store data, which can sometimes lead to information leakage if permissions aren't tight.

## Helpful Reading Material

* Scheduling tasks: [A Guide to Cron and Crontab](https://www.ostechnix.com/a-beginners-guide-to-cron-jobs/)
* Understanding Shell Scripts: [Bash Scripting for Beginners](https://linuxconfig.org/bash-scripting-tutorial-for-beginners)
