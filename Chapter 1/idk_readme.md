# Introduction to C in Linux

## Introduction to C in Linux

This document serves as a thorough guide to understanding the C programming language within the Linux operating system. It explores key concepts, tools, and practices necessary for building efficient and robust C applications in a UNIX-like environment.

### Overview of UNIX

UNIX is a multiuser, multitasking operating system developed in the 1970s at AT&T's Bell Labs. It is designed to allow multiple users to operate simultaneously and run several tasks or programs concurrently. The UNIX file system (FS) is organized hierarchically, resembling an upside-down tree structure with the root directory (/) at the top, branching out into various standard directories such as `/bin`, `/etc`, and `/home`.

## **UNIX File System Structure**

The UNIX file system structure is a hierarchical organization of files and directories, designed to efficiently manage and store data. It resembles an upside-down tree, with the root directory at the top and all other directories branching out from it.

**Key Directories:**

- **`/bin`**: Essential command binaries.
- **`/boot`**: Boot loader files.
- **`/dev`**: Device files.
- **`/etc`**: Configuration files.
- **`/home`**: User home directories.
- **`/lib`**: Shared libraries.
- **`/media`**: Mount points for removable media.

## **Processes and Threads**

- **Process**: An instance of a running program that includes the program code, its current activity, and a set of resources such as memory and file descriptors.
- **Thread**: A lightweight process that allows for parallel execution of tasks within a single application, improving performance and responsiveness.

---

# Chapter 1: Introduction to C in Linux

### Chapter Overview

This chapter provides an overview of the basics of the C programming language within the Linux environment. It covers fundamental concepts such as UNIX, processes and threads, the Linux kernel, system calls, C standards, and the structure of C code.

### What is UNIX?

UNIX is designed to be multiuser and multitasking, allowing multiple users to run several tasks or programs simultaneously.

### Processes and Threads

- **Process**: An instance of a running program that includes its code, current activity, and resources such as memory and file descriptors.
- **Thread**: A lightweight process that allows for parallel execution of tasks within a single application, improving performance and responsiveness.

### The Linux Kernel

The kernel serves as the core component that interfaces between hardware and software applications. It manages system resources, including memory, processing power, and input/output devices.

### System Calls

A system call (syscall) is a programmatic interface through which programs request services from the operating system's kernel.

### C Standards

1. **ANSI C (C89/C90)**: Introduced function prototypes and enhanced type checking.
2. **C99**: Added data types like long long and variable-length arrays.
3. **C11**: Improved multi-threading support with a standardized threading library.

### C Code Structure

1. **Preprocessor Directives**: Commands processed before compilation (e.g., `#include <stdio.h>`).
2. **Global Declarations**: Global variables accessible throughout the program.
3. **Subprograms**: User-defined functions promoting code reusability.
4. **Main Function**: The entry point of every C program.

---

# Chapter 2: Compilation in C Programming

### Chapter Overview

This chapter explores the concept of compilation in C programming, particularly within the Linux environment. It covers various stages involved in compiling a C program, the structure of executable files, CPU scheduling, and build automation tools.

### How Compilation Works

The compilation process involves several stages:

1. **Preprocessing**
    - Handles directives that begin with `#`, removing comments and expanding macros.
    - Command:
        
        ```bash
        gcc -E filename.c -o filename.i
        ```
        
2. **Compiling**
    - Translates preprocessed code into assembly language specific to the target architecture.
    - Command:
        
        ```bash
        gcc -S filename.i -o filename.s
        ```
        
3. **Assembling**
    - Converts assembly code into machine code (object file).
    - Command:
        
        ```bash
        gcc -c filename.s -o filename.o
        ```
        
4. **Linking**
    - Combines object files into a single executable.
    - Command:
        
        ```bash
        gcc filename.o -o executable_name
        ```
        
5. **Loading**
    - Loads the executable into memory for execution.
    - Command to Run Executable:
        
        ```bash
        ./executable_name
        ```
        

## **Summary of Compilation Commands**

| **Step** | **Command** | **Output File** |
| --- | --- | --- |
| Preprocessing | **`gcc -E filename.c -o filename.i`** | **`filename.i`** |
| Compiling | **`gcc -S filename.i -o filename.s`** | **`filename.s`** |
| Assembling | **`gcc -c filename.s -o filename.o`** | **`filename.o`** |
| Linking | **`gcc filename.o -o executable_name`** | **`executable_name`** |
| Execution | **`./executable_name`** | Program output on console |

### Structure of Executable Files

The Executable and Linkable Format (ELF) is the standard file format for executable files in Linux. This format provides a flexible way to store binary files, allowing them to be executed efficiently by the system.

- **ELF Header**
    
    The ELF header is located at the beginning of the file and contains essential metadata, including:
    
    - Magic number to identify the file type.
    - File class (32-bit or 64-bit).
    - Data encoding (endianness).
    - File type (e.g., executable or shared object).
    - Machine architecture.
    - Entry point address.
    - Offsets to program and section header tables.
- **Program Header Table**
    
    This table describes segments that are loaded into memory during execution. Each entry specifies:
    
    - Segment type.
    - Offset in the file where the segment starts.
    - Virtual address where the segment should be loaded in memory.
    - Size of the segment in memory and on disk.
- **Section Header Table**
    
    This table provides information about sections within the ELF file, such as:
    
    - `.text`: Contains executable code.
    - `.data`: Contains initialized variables.
    - `.bss`: Contains uninitialized variables.
- **Data Sections**
    
    These sections contain actual data referenced by entries in both the program header and section header tables, including executable code and initialized variables.
    

### **CPU Scheduling**

CPU scheduling is the process of selecting which processes in the ready queue should be allocated CPU time for execution. The main goal is to maximize CPU utilization while ensuring fairness among processes. Common scheduling algorithms include:

- **First-Come, First-Served (FCFS)**: Processes are scheduled in order of arrival.
- **Shortest Job First (SJF)**: The process with the shortest execution time is scheduled next.
- **Round Robin (RR)**: Each process is given a fixed time slice in a cyclic order.

## **Build Automation Tools**

### **Make Tool**

Make is a build automation tool that helps manage and compile source code into executable programs. It uses a Makefile to define rules and dependencies, allowing it to automatically determine which parts of the code need to be recompiled when changes are made.

### **CMake Tool**

CMake is a cross-platform build system generator that simplifies managing software builds. It uses a configuration file called `CMakeLists.txt` to define project settings and dependencies, allowing developers to generate platform-specific build files from a single set of instructions.

---

## Chapter 2 Exercise:

### Exercise Overview

The compilation process of a C program involves several key stages: preprocessing, compiling, assembling, linking, and loading.

### Example Code Snippet for Factorial Calculation:

```c
#include <stdio.h>

// Function prototype
unsigned long long factorial(int n);

int main() {
    int number;
    unsigned long long result;

    // Prompt user for input
    printf("Enter a positive integer: ");
    scanf("%d", &number);

    // Check for negative input
    if (number < 0) {
        printf("Error: Factorial is not defined for negative numbers.\\n");
        return 1; // Return with an error code
    }

    // Calculate factorial
    result = factorial(number);

    // Display result
    printf("Factorial of %d = %llu\\n", number, result);

    return 0; // Successful completion
}

// Function to calculate factorial recursively
unsigned long long factorial(int n) {
    if (n == 0) {
        return 1; // Base case: 0! = 1
    } else {
        return n * factorial(n - 1); // Recursive case
    }
}

```

### **1. Preprocessing**

**What Happens**: The preprocessor handles directives that begin with `#`, such as `#include` and `#define`. It removes comments and expands macros.

**Commands**:

- To preprocess the code and generate an intermediate file (`.i`):
    
    ```
    gcc -E factorial.c -o factorial.i
    ```
    

**Output**: The `factorial.i` file contains the expanded source code with all header file contents included and comments removed.

### **2. Compiling**

**What Happens**: The compiler translates the preprocessed code into assembly language specific to the target architecture.

**Commands**:

- To compile the preprocessed file into assembly language (`.s`):
    
    ```
    gcc -S factorial.i -o factorial.s
    ```
    

**Output**: The `factorial.s` file contains assembly instructions corresponding to the C code.

### **3. Assembling**

**What Happens**: The assembler converts the assembly language code into machine code, producing an object file (`.o`).

**Commands**:

- To assemble the assembly file into an object file:
    
    ```
    gcc -c factorial.s -o factorial.o
    ```
    

**Output**: The `factorial.o` file contains binary machine code that is not directly human-readable.

### **4. Linking**

**What Happens**: The linker combines one or more object files into a single executable. It resolves references to external functions (like those from libraries).

**Commands**:

- To link the object file and create an executable:
    
    ```
    gcc factorial.o -o factorial
    ```
    

**Output**: The executable file named `factorial` is created, which can be run directly.

### **5. Loading**

After linking, when you run your program, the loader is responsible for loading the executable into memory and preparing it for execution.

**Command to Run Executable**:

```
./factorial
```

### **Goal:**

Understanding each step of the compilation process in C on Linux helps developers optimize their code and troubleshoot issues effectively. Each stage plays a crucial role in transforming high-level source code into an executable binary that can be run on a computer. By manually executing these steps, programmers gain deeper insights into how their code is processed and executed by the system.

---

# Chapter 3: Memory Management in C

### Chapter Overview

This chapter explores critical concepts related to memory management in C programming within the Linux environment.

### Overview of Memory Management

Memory management involves allocation, reallocation, and deallocation during execution and can be categorised into two main types:

- **Virtual Memory**
- **Physical Memory**

### Virtual Memory

Virtual memory allows programs to use more memory than physically available by creating an illusion of contiguous memory space.

Key Features:

- Swapping allows freeing up RAM by moving pages to disk storage when physical memory is full.
- Isolation prevents processes from interfering with each other’s memory.

### Physical Memory

Physical memory refers to actual RAM where data resides during execution.

Characteristics:

- Limited Size based on hardware configuration.
- Faster access compared to disk storage.
- Direct access by CPU using addresses.

### Memory Allocation Techniques

1. **Static Memory Allocation**
    - Allocated at compile time with fixed sizes.
2. **Dynamic Memory Allocation**
    - Uses functions like `malloc()` and `calloc()` for variable-sized data structures.

### **`malloc()`**

- Stands for "memory allocation."
- Allocates a specified number of bytes in memory and returns a pointer to the beginning of the allocated block.
- **Initialization**: Memory allocated by `malloc()` is not initialized; it contains garbage values.
- **Syntax**:
    
    ```
    ptr = (castType*) malloc(size);
    ```
    

### Example Program Using `malloc()`

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *arr;
    int n = 5;

    arr = (int*) malloc(n * sizeof(int));
    if (arr == NULL) {
        printf("Memory allocation failed\\n");
        return 1;
    }

    for (int i = 0; i < n; i++) {
        arr[i] = i + 1; // Assign values from 1 to n
        printf("%d ", arr[i]);
    }

    free(arr); // Free allocated memory
    return 0;
}

```

### **`calloc()`**

- Stands for "contiguous allocation."
- Allocates memory for an array of elements and initializes all bits to zero.
- **Initialization**: Memory allocated by `calloc()` is initialized to zero.
- **Syntax**:
    
    ```
    ptr = (castType*) calloc(n, size);
    ```
    

### Example Program Using `calloc()`

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *arr;
    int n = 5;

    arr = (int*) calloc(n, sizeof(int));
    if (arr == NULL) {
        printf("Memory allocation failed\\n");
        return 1;
    }

    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]); // All values will be initialized to zero
    }

    free(arr); // Free allocated memory
    return 0;
}

```

---

## Chapter 3 Exercise:

### Exercise Overview

In this exercise, you will write a C program demonstrating both `malloc()` and `calloc()` functions for dynamic memory allocation.

### Objectives:

1. Use `malloc()` to allocate memory for an array of integers.
2. Use `calloc()` to allocate memory for another array initialized to zero.
3. Print values stored in both arrays to verify correct allocation.
4. Free allocated memory after use to prevent leaks.

### Sample Code Structure:

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int n;

    // Prompt user for number of elements
    printf("Enter the number of elements: ");
    scanf("%d", &n);

    // Allocate memory using malloc
    int *mallocArray = (int *)malloc(n * sizeof(int));

    if (mallocArray == NULL) {
        printf("Memory allocation using malloc failed\\n");
        return 1; // Exit if allocation fails
    }

    // Allocate memory using calloc
    int *callocArray = (int *)calloc(n, sizeof(int));

    if (callocArray == NULL) {
        printf("Memory allocation using calloc failed\\n");
        free(mallocArray); // Free previously allocated memory
        return 1; // Exit if allocation fails
    }

    // Fill mallocArray with values from 1 to n
    for (int i = 0; i < n; i++) {
        mallocArray[i] = i + 1;
        printf("%d ", mallocArray[i]);
    }

   printf("\\n");

   // Print values from callocArray (should be all zeros)
   printf("Values in callocArray: ");
   for (int i = 0; i < n; i++) {
       printf("%d ", callocArray[i]);
   }
   printf("\\n");

   // Free allocated memory
   free(mallocArray);
   free(callocArray);

   return 0;
}

```

### **Submission**

Once you have completed the exercise, compile your program using GCC:

```
gcc -o memory_management memory_management.c
```

Run your program:

```
./memory_management
```

Make sure to test your program with different input values to ensure it works correctly.

### **Additional Resources**

For more details and examples, refer to the GitHub repository linked in Chapter 3:

[GitHub Repository](https://github.com/myselfbasil/Introduction-to-C-in-Linux)

---

Drop a 🖤 if you can. Thank you reading this.
