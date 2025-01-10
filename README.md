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

The program performs the following tasks:

Counts lines, words, and characters in files specified via command-line arguments.

Supports reading from stdin when no files are provided.

Includes options to display specific counts (-l, -w, -c).

Handles errors and edge cases gracefully.


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

1. Single File
Command: ./word_count file.txt
Expected Output: Line, word, and character counts for file.txt.


2. Multiple Files
Command: ./word_count file1.txt file2.txt
Expected Output: Individual counts for each file and a summary total.


3. Standard Input
Command: ./word_count
Input: Text via stdin.
Expected Output: Line, word, and character counts for the input text.



