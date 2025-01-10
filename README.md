# Project-15: Operating System Calls (copy and wc)

## Group Information

**Group Number**: [15]  
**Group Members and Index Numbers**:  
- Member 1: [Amna Abbass HassanBasheer], [18-635]  
- Member 2: [Samah Adil Mohamed Abdelaal], [17-645]  
- Member 3: [Yousif hafiz abdalwahab hafiz],[18-626]
-Member 4 :[Noor Tilal Mohammed Ahmed],[18-625]

---

## Project Description

This project implements two system utilities using basic operating system calls:

1. **my_copy**: A program replicating the functionality of the `cp` command.
2. **word_count**: A program replicating the functionality of the `wc` command.

### Objectives
- Enhance understanding of system calls (`open`, `read`, `write`, `close`, `fstat`).
- Handle command-line arguments effectively.
- Implement robust error handling and program interaction.

---

## Design Overview

### **my_copy**
The program performs the following tasks:
- Copies a source file to a destination file, ensuring both files are of equal size.
- Includes an option `-p` to copy file permissions using `fstat`.
- Handles missing or invalid arguments with appropriate user guidance.
- Prompts for overwrite confirmation if the destination file exists.
- Ensures cleanup during interruptions (e.g., `Ctrl+C`).

#### Core Functionality
```c
int my_copy(int source_fd, int dest_fd);

This function copies content between file descriptors.


---

# word_count

This program is a simple implementation of the wc command. It counts the number of lines, words, and characters (bytes) in text files provided as command-line arguments or reads from standard input if no files are specified. The program also supports options to display specific counts (-l for lines, -w for words, -c for characters).
 
## Features 

Count lines, words, and characters from one or multiple files.

Display individual file counts and the total for all files.

Read from standard input if no files are specified.

Options to show specific counts (-l, -w, -c).

Handles error conditions like inaccessible files gracefully.

Requirements

C compiler

POSIX-compliant operating system (Linux, macOS, etc.)

Options

-l: Display the number of lines.

-w: Display the number of words.

-c: Display the number of characters (bytes).

If no options are specified, all counts (lines, words, characters) are displayed.

Error Handling

Displays an error message if a file cannot be opened.

Gracefully handles invalid input and unknown options.



# Core Functionality

int word_count(int fd, int *lines, int *words, int *bytes);

This function calculates line, word, and byte counts from a file descriptor.


---

## Complete Specification

Ambiguities Addressed

Permission Copying: Uses the fstat system call to match the destination file's permissions with the source file.

User Prompts: Overwrite confirmation is case-insensitive (Y/y for yes, N/n or Enter for no).

Error Handling: Comprehensive handling of missing arguments, invalid file paths, and unexpected signals.



---

## Known Bugs or Problems

No identified bugs or missing features at the time of submission.



---

# Testing

## my_copy

1. Basic Copying
Command: ./my_copy source.txt dest.txt
Expected Output: File copied successfully.


2. Permission Copying
Command: ./my_copy -p source.txt dest.txt
Expected Output: Destination file permissions match source file.


3. Overwrite Confirmation
Command: ./my_copy source.txt dest.txt
Scenario: Destination file exists.
Input: Y or N
Expected Output: File overwritten or process exited without copying.


4. Error Handling

Missing arguments or invalid files.





---

## word_count

The program has been tested with the following scenarios:
Test Case 1: Single line, single word
Test Case 2: Multiple lines and words
Test Case 3: Empty file
Test Case 4: File with only spaces and newlines
Test Case 5: File with mixed content