# Introduction to C in Linux

This repository contains the materials and examples from the "Introduction to C in Linux" lecture presented by Prof. S.E. Vinodh Edwards. The presentation covers fundamental concepts of the C programming language, its compilation process, and its integration with Linux.

## Table of Contents

1. [Introduction](#introduction)
2. [UNIX Overview](#unix-overview)
3. [Processes and Threads](#processes-and-threads)
4. [Linux Kernel](#linux-kernel)
5. [System Calls](#system-calls)
6. [C Standards](#c-standards)
7. [C Code Structure](#c-code-structure)
8. [Compilation Process](#compilation-process)
9. [Executable File Structure](#executable-file-structure)
10. [CPU Scheduling](#cpu-scheduling)
11. [Build Automation Tools](#build-automation-tools)
12. [Challenge](#challenge)

## Introduction

This section introduces the basics of C programming within the Linux environment, providing foundational knowledge necessary for further exploration of the language.

## UNIX Overview

UNIX is a multiuser and multitasking operating system developed in the 1970s at AT&T's Bell Labs. It allows multiple users to run several tasks or programs simultaneously.

### UNIX File System Structure

The UNIX file system is organized hierarchically, resembling an upside-down tree with the root directory (/) at the top. Key directories include `/bin`, `/boot`, `/dev`, `/etc`, `/home`, `/lib`, and `/media`.

## Processes and Threads

- **Process**: An instance of a running program, including its code, current activity, and resources like memory and file descriptors.
- **Thread**: A lightweight process that allows parallel execution of tasks within a single application, improving performance and responsiveness.

## Linux Kernel

The kernel is the core component of the Linux operating system, serving as the interface between hardware and software applications. It manages system resources such as memory, processing power, and input/output devices.

## System Calls

A system call (syscall) is an interface through which a program requests services from the operating system's kernel.

## C Standards

1. **ANSI C (C89/C90)**: Introduced function prototypes and enhanced type checking.
2. **C99**: Added new data types and variable-length arrays.
3. **C11**: Improved support for multi-threading and atomic operations.

## C Code Structure

1. **Preprocessor Directives**: Commands processed before compilation (e.g., `#include <stdio.h>`).
2. **Global Declarations**: Global variables and function prototypes accessible throughout the program.
3. **Subprograms**: User-defined functions for specific tasks.
4. **Main Function**: The entry point of every C program.

## Compilation Process

The compilation process involves several stages:

1. **Preprocessing**: Handles directives like `#include` and `#define`.
2. **Compiling**: Translates preprocessed code into assembly language.
3. **Assembling**: Converts assembly code into machine code (object file).
4. **Linking**: Combines object files into a single executable.
5. **Loading**: Loads the executable into memory for execution.

### Summary of Compilation Steps

You can compile a C program using a single command:
```bash
gcc filename.c -o output_executable
```

## Executable File Structure

The Executable and Linkable Format (ELF) is the standard file format for executable files in Linux, containing essential metadata such as:

- **ELF Header**
- **Program Header Table**
- **Section Header Table**
- **Data Sections**

## CPU Scheduling

CPU scheduling determines which processes in the ready queue should be allocated CPU time for execution, utilizing various algorithms such as:

- First-Come, First-Served (FCFS)
- Shortest Job First (SJF)
- Round Robin (RR)

## Build Automation Tools

### Make

Make is a build automation tool that manages and compiles source code into executable programs using a Makefile to define rules and dependencies.

### CMake

CMake is a cross-platform build system generator that simplifies project management by using a configuration file (`CMakeLists.txt`) to define settings and generate platform-specific build files.

## Challenge

You are required to compile a C program following the steps outlined in this presentation. A sample program can be found in this GitHub repository.

---

Feel free to explore the repository for additional resources and examples related to C programming in Linux!
```
