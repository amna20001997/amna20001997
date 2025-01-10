
# Pipe Execution Program

## Objective
This project demonstrates how to:
1. Use the `fork()` system call to create child processes.
2. Establish a pipe between two processes for inter-process communication (IPC).
3. Redirect data from one process to another using `dup()` and `dup2()` system calls.

---

## Group Information
- **Group Number**: 16
- **Index Numbers**:
17-645
18-626
18-625
18-635   
- **Members**:
1_ Samah Adil Mohamed Abdelaal 17-645
2_ Amna Abbas Hassan Bashir 18-635
3_ Yousif hafiz abdalwahab hafiz 18-626
4_Noor Tilal Mohammed Ahmed 18-625  

---

## Work Division
- **[Member 1]**: Implemented the creation of pipes and child processes  
- **[Member 2]**: work with member 1 in problem 1 , implemented the creation of pipes and child processes
- **[Member 3]**: Implemented the creation of Problem 2 
- **[Member 4]**: Sharing in Coding of Problem 2 and Created this README file and documented the design overview.  

---
## Design Overview
### Problem 1
1. **Child Process Creation**:  
   Create two child processes from the same parent process.

2. **Parent Process Behavior**:  
   - Waits for both child processes to terminate.  
   - Prints the exit status of each child upon termination.

### Problem 2
1. **Command Parsing**:  
   Separate commands based on the pipe (`|`) character.

2. **Pipe Creation**:  
   Use the `pipe()` system call to establish communication between processes.

3. **Child Processes Execution**:  
   - The first child executes the command before the pipe.  
   - The second child executes the command after the pipe and reads input from the first command.

4. **Parent Process Behavior**:  
   Waits for both child processes to finish execution.

5. **Error Handling**:  
   Handle invalid commands or unexpected inputs.

---

## Complete Specification
### Problem 1
1. Create two child processes from the same parent process.
2. Ensure the parent waits for both child processes to complete.
3. Print the exit status of each child upon termination.

### Problem 2
1. Execute commands passed as command-line arguments separated by a pipe (`|`).
2. The first child executes the first command and passes its output through the pipe.
3. The second child reads the input from the pipe and executes the second command.
4. The parent waits for both child processes to finish.

---

## Testing
### Functionality Testing
1. **Valid Commands**:  
   Example: `ls | grep .c`  
   Expected Output: Files matching the pattern `.c` are listed.

2. **Invalid Commands**:  
   Example: `invalid_cmd | grep`  
   Expected Output: Error message indicating an invalid command.

3. **Error Handling**:  
   Simulate pipe creation failure and verify proper error messages.

4. **Edge Cases**:  
   Empty input or no pipe character results in an error.

---

## Known Bugs or Limitations
1. The program does not handle multiple pipes (e.g., `ls | grep | wc`).
2. Partial handling of commands with excessive arguments or invalid syntax.

---

## Pre-requisites
1. Familiarity with system calls (`fork`, `wait`, `pipe`, `dup`, `dup2`, `execvp`).
2. Knowledge of inter-process communication (IPC).
3. Ability to read Unix manual pages.

---

## Test Cases
### Problem 1
1. **Two child processes successfully created**:  
   Input: Test program logic for child creation.  
   Output: Parent waits and prints exit statuses of both children.

### Problem 2
1. **Valid Command Execution**:  
   Input: `ls | wc`  
   Output: Correct word count.

2. **Invalid Command Handling**:  
   Input: `invalid_cmd | wc`  
   Output: Error message.

3. **Pipe Failure**:  
   Simulate pipe creation failure during execution.

## Compilation and Execution
To compile the program:
```bash
make

To run the program with commands:

./pipe_program "command1 | command2"

For example:
./pipe_program "ls | wc -l"

