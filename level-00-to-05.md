# Bandit Walkthroughs: Levels 00 – 05

## Level 0 → Level 1

### Objective
Connect to the remote Bandit server via SSH and retrieve the password for Level 1 stored inside the `readme` file.

### Commands Used
* `ssh` — Connected securely to the remote OverTheWire server on port `2220`.
* `ls` — Listed the files inside the home directory.
* `cat` — Printed the contents of the `readme` file to the terminal.

### Step-by-Step Walkthrough
1. Connected to Level 0 using `ssh bandit0@bandit.labs.overthewire.org -p 2220` and logged in with the password `bandit0`.
2. Ran `ls` to view the directory contents and spotted a file named `readme`.
3. Executed `cat readme` to read the file and retrieved the password for `bandit1` (`[REDACTED]`).

### Key Takeaway
* Standard Linux directories can be inspected immediately after login using `ls`, and plain-text files can be read directly in the terminal with `cat`.

---

## Level 1 → Level 2

### Objective
*(Write the goal for Level 1 here)*

### Commands Used
* `command` — *(What it did)*

### Step-by-Step Walkthrough
1. Logged into `bandit1` via SSH.
2. *(Add your steps here)*
3. Retrieved the password for `bandit2` (`[REDACTED]`).

### Key Takeaway
* *(Add what you learned here)*

---

## Level 2 → Level 3

### Objective
*(Write the goal for Level 2 here)*

### Commands Used
* `command` — *(What it did)*

### Step-by-Step Walkthrough
1. Logged into `bandit2` via SSH.
2. *(Add your steps here)*
3. Retrieved the password for `bandit3` (`[REDACTED]`).

### Key Takeaway
* *(Add what you learned here)*

---

## Level 3 → Level 4

### Objective
*(Write the goal for Level 3 here)*

### Commands Used
* `command` — *(What it did)*

### Step-by-Step Walkthrough
1. Logged into `bandit3` via SSH.
2. *(Add your steps here)*
3. Retrieved the password for `bandit4` (`[REDACTED]`).

### Key Takeaway
* *(Add what you learned here)*

---

## Level 4 → Level 5

### Objective
*(Write the goal for Level 4 here)*

### Commands Used
* `command` — *(What it did)*

### Step-by-Step Walkthrough
1. Logged into `bandit4` via SSH.
2. *(Add your steps here)*
3. Retrieved the password for `bandit5` (`[REDACTED]`).

### Key Takeaway
* *(Add what you learned here)*
