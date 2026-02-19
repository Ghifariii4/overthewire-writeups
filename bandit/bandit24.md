# Bandit23 -> 24: Writing Your Own Cron Job

[Challenge](https://overthewire.org/wargames/bandit/bandit23.html)

## Level Description

A program is running periodically from **cron**. Check **/etc/cron.d/** for the configuration. This time, the cron job executes all scripts found in a specific directory: **/var/spool/bandit24/foo/**. You need to write a script that will grab the password for you.

## The Process

This level is a major step up because instead of just *reading* a script, I had to *write* one. The cron job for this level is configured to execute any script it finds in a specific folder and then delete it.

First, I checked the cron script to see how it works:

```bash
$ cat /usr/bin/cronjob_bandit24.sh

```

The script essentially says: "Look in `/var/spool/bandit24/foo/`, execute every script there as user **bandit24**, and then delete the scripts."

### The Strategy

I needed to create a script that, when run by bandit24, would copy the password file I couldn't normally see into a place where I could.

1. **Create a workspace**:
```bash
$ mkdir /tmp/my_secret_spot
$ chmod 777 /tmp/my_secret_spot

```


2. **Write the exploit script**:
I created a file named `solve.sh` inside my temp folder:
```bash
#!/bin/bash
cat /etc/bandit_pass/bandit24 > /tmp/my_secret_spot/password.txt

```


3. **Set permissions**:
I had to make sure the script was executable by the cron user:
```bash
$ chmod 777 solve.sh

```


4. **Deploy**:
I copied my script into the "spool" directory where the cron job looks for work:
```bash
$ cp solve.sh /var/spool/bandit24/foo/

```



Now, I just had to wait a minute for the cron job to run. Once a minute passed, I checked my temp folder, and `password.txt` was there waiting for me!

## Password For the Next Level

`[SPOILER]`

## What I Learned

* **Insecure Spooling**: I learned that if a high-privilege user automatically executes scripts from a world-writable directory, a lower-privilege user can easily "hijack" those privileges.
* **chmod 777**: While usually dangerous, I learned when it's necessary to make a directory "wide open" so two different users can read/write to it.
* **Automation Exploitation**: This level demonstrated how attackers look for scheduled tasks to gain higher levels of access.

## Helpful Reading Material

* Basic Shell Scripting: [Writing your first shell script](https://www.freecodecamp.org/news/shell-scripting-crash-course-how-to-write-bash-scripts-in-linux/)
* Understanding /var/spool: [The Linux Directory Structure](https://www.howtogeek.com/117435/htg-explains-the-linux-directory-structure-explained/)
