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
Locate and read a file named `-` (a single dash) inside the home directory to retrieve the password for Level 2.

### Commands Used
* `ls` — Verified the file named `-` was present in the directory.
* `cat < -` — Used standard input redirection to feed the contents of `-` directly into `cat`.

### Step-by-Step Walkthrough
1. Logged into `bandit1` via SSH using the password retrieved from Level 0.
2. Recognized that running `cat -` directly fails because Linux interprets `-` as a command-line option for standard input rather than a file.
3. Used standard input redirection (`cat < -`) to pass the file contents to `cat` and retrieved the password for `bandit2` (`[REDACTED]`).

### Key Takeaway
* Special filenames starting with dashes cannot be passed directly as normal arguments; input redirection (`<`) or relative paths (`./-`) prevent the shell from treating them as flags.

---

## Level 2 → Level 3

### Objective
Read a file containing both leading dashes and spaces (`--spaces in this filename--`) to retrieve the password for Level 3.

### Commands Used
* `ls` — Identified the exact filename containing spaces and leading dashes.
* `cat "./--spaces in this filename--"` / `cat ./--spaces\ in\ this\ filename--` — Used relative paths combined with quotes or backslash escaping to read the file.

### Step-by-Step Walkthrough
1. Logged into `bandit2` via SSH.
2. Listed the directory contents and observed `--spaces in this filename--`.
3. Prevented the Bash shell from splitting the filename at each space by using double quotes (`" "`) and backslash escaping (`\ `), along with `./` to handle the leading dashes, retrieving the password for `bandit3` (`[REDACTED]`).

### Key Takeaway
* The Linux shell splits arguments at spaces by default; wrapping paths in double quotes or escaping spaces with a backslash (`\`) forces the shell to treat the entire name as a single file.

---

## Level 3 → Level 4

### Objective
Locate and read a hidden file inside the `inhere` directory to retrieve the password for Level 4.

### Commands Used
* `cd inhere` — Changed into the `inhere` target directory.
* `ls -a` — Listed all files in the directory, including hidden dotfiles.
* `cat ...Hiding-From-You` — Displayed the contents of the hidden file.

### Step-by-Step Walkthrough
1. Logged into `bandit3` via SSH and navigated into the `inhere` directory using `cd inhere`.
2. Ran `ls -a` to reveal hidden files starting with a dot and discovered `...Hiding-From-You`.
3. Read the hidden file with `cat ...Hiding-From-You` and retrieved the password for `bandit4` (`[REDACTED]`).

### Key Takeaway
* Files beginning with a period (`.`) are hidden from standard `ls` output; adding the `-a` flag reveals all hidden configuration and system files.

---

## Level 4 → Level 5

### Objective
Identify the single human-readable text file among multiple binary files inside the `inhere` directory to retrieve the password for Level 5.

### Commands Used
* `cd inhere` — Navigated into the `inhere` directory.
* `file ./*` — Inspected the file type of every item in the directory simultaneously.
* `cat ./-file07` — Printed the contents of the identified ASCII text file.

### Step-by-Step Walkthrough
1. Logged into `bandit4` via SSH and moved into the `inhere` folder.
2. Ran `file ./*` to safely check the data type of every dashed file without printing raw binary data to the terminal.
3. Identified `-file07` as `ASCII text` and read it using `cat ./-file07` to retrieve the password for `bandit5` (`[REDACTED]`).

### Key Takeaway
* The `file` utility inspects file headers to identify file types safely, and wildcard expansion with a relative path (`./*`) handles multiple dashed filenames at once.
