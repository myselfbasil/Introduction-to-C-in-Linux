# Chapter 1: Introduction to C in Linux

This chapter provides an overview of the basics of the C programming language within the Linux environment. It covers fundamental concepts such as UNIX, processes and threads, the Linux kernel, system calls, C standards, and the structure of C code.

## Table of Contents

1. [What is UNIX?](#what-is-unix)
2. [UNIX File System Structure](#unix-file-system-structure)
3. [Processes and Threads](#processes-and-threads)
4. [Linux Kernel](#linux-kernel)
5. [System Calls](#system-calls)
6. [C Standards](#c-standards)
7. [C Code Structure](#c-code-structure)

## What is UNIX?

UNIX is an operating system developed in the 1970s at AT&T's Bell Labs. It is designed to be multiuser and multitasking, allowing multiple users to run several tasks or programs simultaneously.

## UNIX File System Structure

The UNIX file system (FS) structure is a hierarchical organization of files and directories, resembling an upside-down tree with the root directory at the top. The root directory (/) serves as the starting point for all other files and directories in the system.

### Key Directories

Some standard directories inside the root include:
- `/bin`: Essential command binaries.
- `/boot`: Boot loader files.
- `/dev`: Device files.
- `/etc`: Configuration files.
- `/home`: User home directories.
- `/lib`: Shared libraries.
- `/media`: Mount points for removable media.

## Processes and Threads

### Process
A **process** is an instance of a running program that includes its code, current activity, and resources such as memory and file descriptors.

### Threads
A **thread** is a lightweight process that allows for parallel execution of tasks within a single application, improving performance and responsiveness.

## Linux Kernel

The kernel of the Linux operating system serves as the core component that interfaces between the computer's hardware and software applications. It manages system resources, including memory, processing power, and input/output devices.

## System Calls

A **system call** (often abbreviated as syscall) is a programmatic interface through which a computer program requests a service from the operating system's kernel. This mechanism allows user applications to perform operations that require higher privileges.

## C Standards

1. **ANSI C (C89/C90)**:
   - Introduced function prototypes.
   - Enhanced type checking.
   - Added standard library functions and headers.
   - Established formal syntax and semantics for the language.

2. **C99**:
   - Introduced new data types: `long long`, `_Bool`, `_Complex`, `_Imaginary`.
   - Added support for variable-length arrays (VLAs).

3. **C11**:
   - Improved support for multi-threading with a standardized threading library (`<threads.h>`).
   - Introduced atomic operations through `<stdatomic.h>`.
   - Added type-generic expressions using the `_Generic` keyword.
   - Enhanced Unicode support.

## C Code Structure

1. **Preprocessor Directives**: Commands processed before compilation, such as `#include <stdio.h>` to include header files or `#define PI 3.14` to define constants.

2. **Global Declarations**: Global variables and function prototypes accessible throughout the program.

3. **Subprograms**: User-defined functions that perform specific tasks, promoting code reusability.

4. **Main Function**: The entry point of every C program where execution begins, typically defined as:
   ```c
   int main() {
       // code
       return 0;
   }