# Bandit Walkthroughs: Levels 00 – 05

## Level 0 → Level 1

**Goal:** Find the password for Level 1 inside the `readme` file.

**Commands Used:**
* `ssh` – Connected to the remote server.
* `ls` – Listed the files in the folder.
* `cat` – Read the text inside the file.

**Steps:**
1. Logged into `bandit0` over SSH on port `2220`.
2. Typed `ls` and saw a file called `readme`.
3. Typed `cat readme` to read the file and get the password for `bandit1` (`[REDACTED]`).

**What I Learned:** Use `ls` to see what is inside a folder and `cat` to read text files.

---

## Level 1 → Level 2

**Goal:** Read a file named `-` (a single dash) to get the password for Level 2.

**Commands Used:**
* `ls` – Confirmed the `-` file was in the folder.
* `cat < -` – Fed the `-` file directly into `cat`.

**Steps:**
1. Logged into `bandit1` over SSH.
2. Typing `cat -` failed because Linux treats `-` as a special option instead of a file name.
3. Used `cat < -` to force the terminal to read the file and show the password for `bandit2` (`[REDACTED]`).

**What I Learned:** Files named with a dash cannot be opened normally. Using `<` (input redirection) or `./-` tells Linux to treat it as a real file.

---

## Level 2 → Level 3

**Goal:** Read a file with spaces and dashes in its name (`--spaces in this filename--`).

**Commands Used:**
* `ls` – Found the exact file name.
* `cat "./--spaces in this filename--"` – Used quotes and `./` to open the file safely.

**Steps:**
1. Logged into `bandit2` over SSH.
2. Found the file `--spaces in this filename--`.
3. Put `./` at the start to handle the dashes, and wrapped the name in quotes (`" "`) so the spaces did not split the command. Retrieved the password for `bandit3` (`[REDACTED]`).

**What I Learned:** Linux splits commands wherever there is a space. Wrapping a file name in quotes or using backslashes (`\ `) keeps the whole name together.

---

## Level 3 → Level 4

**Goal:** Find and read a hidden file inside the `inhere` folder.

**Commands Used:**
* `cd inhere` – Opened the `inhere` folder.
* `ls -a` – Showed all files, including hidden ones.
* `cat ...Hiding-From-You` – Read the hidden file.

**Steps:**
1. Logged into `bandit3` and moved into the `inhere` folder using `cd inhere`.
2. Typed `ls -a` to reveal hidden files starting with a dot and spotted `...Hiding-From-You`.
3. Typed `cat ...Hiding-From-You` to get the password for `bandit4` (`[REDACTED]`).

**What I Learned:** Files starting with a dot (`.`) are hidden by default. Adding `-a` to `ls` reveals everything.

---

## Level 4 → Level 5

**Goal:** Find the only human-readable text file inside the `inhere` folder.

**Commands Used:**
* `cd inhere` – Opened the `inhere` folder.
* `file ./*` – Checked the file type of every file in the folder at once.
* `cat ./-file07` – Read the text file.

**Steps:**
1. Logged into `bandit4` and moved into the `inhere` folder.
2. Ran `file ./*` to check every file without printing messy binary code to the screen.
3. Saw that `-file07` was `ASCII text`, then ran `cat ./-file07` to get the password for `bandit5` (`[REDACTED]`).

**What I Learned:** The `file` command safely tells you what kind of data is inside a file before you open it.
