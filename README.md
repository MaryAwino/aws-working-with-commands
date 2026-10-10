# AWS Working with Commands

## Overview

This lab focuses on essential Linux command-line operations performed on an Amazon Linux EC2 instance using SSH. It demonstrates how to manipulate text, process CSV files, and combine commands using pipes.

## Objectives

- Use `tee` to display and save command output.
- Use `sort` to sort CSV records.
- Use the pipe operator (`|`) to pass output between commands.
- Use `cut` to extract specific fields from text.
- Use `sed` to perform text substitutions.

## Environment

- **Cloud Provider:** Amazon Web Services (AWS)
- **Compute Service:** Amazon EC2
- **Operating System:** Amazon Linux
- **Access Method:** SSH using PuTTY
- **Working Directory:** `/home/ec2-user`

## Task 1: Connect to an EC2 Instance

Connected to an Amazon Linux EC2 instance using SSH and verified the working directory.

Command:

```bash
pwd
```

Expected output:

```text
/home/ec2-user
```

## Task 2: Use the tee Command

### Objective
Display the hostname in the terminal and save it to a file simultaneously.

Command:

```bash
hostname | tee file1.txt
```

Verification:

```bash
ls
```

The `tee` command reads input from the pipe, displays it on the terminal, and writes it to `file1.txt`.

## Task 3: Use sort and the Pipe Operator

### Create a CSV file

```bash
cat > test.csv
```

Enter the following records, then press `Ctrl+D`:

```text
Factory, 1, Paris
Store, 2, Dubai
Factory, 3, Brasilia
Store, 4, Algiers
Factory, 5, Tokyo
```

### Sort the records

```bash
sort test.csv
```

The command sorts the records alphabetically by their complete lines.

### Search for Paris using a pipe

```bash
cat test.csv | grep Paris
```

Expected output:

```text
Factory, 1, Paris
```

The pipe passes the output of `cat` to `grep`, which searches for the text `Paris`.

## Task 4: Use the cut Command

### Create a CSV file

```bash
cat > cities.csv
```

Enter the following records, then press `Ctrl+D`:

```text
Dallas, Texas
Seattle, Washington
Los Angeles, California
Atlanta, Georgia
New York, New York
```

### Extract the city names

```bash
cut -d ',' -f 1 cities.csv
```

Expected output:

```text
Dallas
Seattle
Los Angeles
Atlanta
New York
```

The `-d ','` option specifies the comma as the delimiter, while `-f 1` extracts the first field.

## Task 5: Additional Challenge — Use sed

### Replace the first comma in cities.csv

Command:

```bash
sed 's/,/./' cities.csv
```

Expected output:

```text
Dallas. Texas
Seattle. Washington
Los Angeles. California
Atlanta. Georgia
New York. New York
```

### Replace the first comma in test.csv

Command:

```bash
sed 's/,/./' test.csv
```

Expected output:

```text
Factory. 1, Paris
Store. 2, Dubai
Factory. 3, Brasilia
Store. 4, Algiers
Factory. 5, Tokyo
```

The `sed` substitution expression replaces the first matching comma on each line with a period. By default, the command displays the transformed output without modifying the original file.

## Key Learnings

- `tee` writes command output to both the terminal and a file.
- `sort` arranges lines alphabetically.
- Pipes (`|`) connect commands so one command's output becomes another command's input.
- `grep` searches text for a specified pattern.
- `cut` extracts selected fields using a delimiter.
- `sed` performs text substitutions on input.

## Conclusion

This lab provided practical experience with Linux command-line tools for text processing and file manipulation on an AWS EC2 instance. These skills are useful for system administration, troubleshooting, log analysis, and automation.

## Skills Demonstrated

Linux | Amazon EC2 | SSH | Bash | Text Processing | CSV Manipulation | Command Pipelines

