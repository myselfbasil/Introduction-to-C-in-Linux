# Chapter 2: Compilation in C Programming

This chapter explores the concept of compilation in C programming, particularly within the Linux environment. It covers the various stages involved in compiling a C program, the structure of executable files, CPU scheduling, and build automation tools.

## Table of Contents

1. [How Compilation Works](#how-compilation-works)
   - [Preprocessing](#preprocessing)
   - [Compiling](#compiling)
   - [Assembling](#assembling)
   - [Linking](#linking)
   - [Loading](#loading)
2. [Structure of Executable Files](#structure-of-executable-files)
   - [ELF Header](#elf-header)
   - [Program Header Table](#program-header-table)
   - [Section Header Table](#section-header-table)
   - [Data Sections](#data-sections)
3. [CPU Scheduling](#cpu-scheduling)
4. [Build Automation Tools](#build-automation-tools)
   - [Make Tool](#make-tool)
   - [CMake Tool](#cmake-tool)
5. [Challenge](#challenge)

## How Compilation Works

The compilation process involves several stages that transform C source code into an executable program:

### Preprocessing
- **What Happens**: The preprocessor handles directives that begin with `#`, such as `#include` and `#define`. It removes comments and expands macros.
- **Command**: To preprocess the code and generate an intermediate file (.i):
  ```bash
  gcc -E filename.c -o filename.i
  ```
- **Output**: The `filename.i` file contains the expanded source code with all header file contents included and comments removed.

### Compiling
- **What Happens**: The compiler translates the preprocessed code into assembly language specific to the target architecture.
- **Command**: To compile the preprocessed file into assembly language (.s):
  ```bash
  gcc -S filename.i -o filename.s
  ```
- **Output**: The `filename.s` file contains assembly instructions corresponding to the C code.

### Assembling
- **What Happens**: The assembler converts the assembly language code into machine code, producing an object file (.o).
- **Command**: To assemble the assembly file into an object file:
  ```bash
  gcc -c filename.s -o filename.o
  ```
- **Output**: The `filename.o` file contains binary machine code that is not directly human-readable.

### Linking
- **What Happens**: The linker combines one or more object files into a single executable. It resolves references to external functions (like those from libraries).
- **Command**: To link the object file and create an executable:
  ```bash
  gcc filename.o -o executable_name
  ```
- **Output**: The executable file named `executable_name` is created, which can be run directly.

### Loading
After linking, when you run your program, the loader is responsible for loading the executable into memory and preparing it for execution.
- **Command to Run Executable**:
  ```bash
  ./executable_name
  ```

## Structure of Executable Files

The Executable and Linkable Format (ELF) is the standard file format for executable files in Linux. This format provides a flexible way to store binary files, allowing them to be executed efficiently by the system.

### ELF Header
The ELF header is located at the beginning of the file and contains essential metadata, including:
- Magic number to identify the file type.
- File class (32-bit or 64-bit).
- Data encoding (endianness).
- File type (e.g., executable or shared object).
- Machine architecture.
- Entry point address.
- Offsets to program and section header tables.

### Program Header Table
This table describes segments that are loaded into memory during execution. Each entry specifies:
- Segment type.
- Offset in the file where the segment starts.
- Virtual address where the segment should be loaded in memory.
- Size of the segment in memory and on disk.

### Section Header Table
This table provides information about sections within the ELF file, such as:
- `.text`: Contains executable code.
- `.data`: Contains initialized variables.
- `.bss`: Contains uninitialized variables.

### Data Sections
These sections contain actual data referenced by entries in both the program header and section header tables, including executable code and initialized variables.

## CPU Scheduling

CPU scheduling is the process of selecting which processes in the ready queue should be allocated CPU time for execution. The main goal is to maximize CPU utilization while ensuring fairness among processes. Common scheduling algorithms include:
- **First-Come, First-Served (FCFS)**: Processes are scheduled in order of arrival.
- **Shortest Job First (SJF)**: The process with the shortest execution time is scheduled next.
- **Round Robin (RR)**: Each process is given a fixed time slice in a cyclic order.

## Build Automation Tools

### Make Tool
Make is a build automation tool that helps manage and compile source code into executable programs. It uses a Makefile to define rules and dependencies, allowing it to automatically determine which parts of the code need to be recompiled when changes are made.

### CMake Tool
CMake is a cross-platform build system generator that simplifies managing software builds. It uses a configuration file called `CMakeLists.txt` to define project settings and dependencies, allowing developers to generate platform-specific build files from a single set of instructions.

## Challenge

You are required to compile a C program following the steps outlined in this chapter. A sample program can be found in this repository.

---

Feel free to explore this repository for additional resources related to compilation in C programming within Linux!
```
