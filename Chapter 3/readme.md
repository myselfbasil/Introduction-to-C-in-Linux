## Chapter 3: Memory Management in C

This chapter explores the critical concept of memory management in C programming within the Linux environment. It covers fundamental aspects such as types of memory, memory allocation techniques, and the structure of memory in C programs.

### Overview of Memory Management

Memory management is a vital aspect of C programming that involves the allocation, reallocation, and deallocation of memory during a program's execution. It can be categorized into two main types:

- **Virtual Memory**
- **Physical Memory**

### Virtual Memory

Virtual memory is an abstraction that allows a program to use more memory than is physically available on the system. It creates an illusion for users that there is a large, contiguous block of memory available, even if the actual physical memory (RAM) is limited.

**Key Features of Virtual Memory:**

- **Swapping**: When physical memory is full, the operating system can swap pages of memory to disk storage (swap space) to free up RAM for other processes.
- **Isolation**: Each process operates in its own virtual address space, preventing them from interfering with each other’s memory.

### Physical Memory

Physical memory refers to the actual RAM installed in a computer system. It is where data and programs reside when they are actively being used by the CPU.

**Characteristics of Physical Memory:**

- **Limited Size**: The amount of physical memory is finite and depends on the hardware configuration.
- **Speed**: Accessing data in physical memory is significantly faster than accessing data on disk storage.
- **Direct Access**: The CPU accesses physical memory directly using addresses.

### Memory Allocation in C

C provides mechanisms for both static and dynamic memory allocation:

1. **Static Memory Allocation**
   - Memory for variables is allocated at compile time. The size must be known beforehand and cannot change during runtime.

2. **Dynamic Memory Allocation**
   - Allows programs to request memory at runtime, essential for handling variable-sized data structures like arrays and linked lists. Key functions include `malloc()` and `calloc()`.

#### `malloc()`

- Stands for "memory allocation."
- Allocates a specified number of bytes in memory and returns a pointer to the beginning of the allocated block.
- **Initialization**: Memory allocated by `malloc()` is not initialized; it contains garbage values.
- **Syntax**: 
  ```c
  ptr = (castType*) malloc(size);
  ```

#### Sample Program Using `malloc()`

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *arr;
    int n = 5;

    arr = (int*) malloc(n * sizeof(int));
    if (arr == NULL) {
        printf("Memory allocation failed\n");
        return 1;
    }

    // Use the allocated array
    for (int i = 0; i < n; i++) {
        arr[i] = i + 1;
        printf("%d ", arr[i]);
    }

    free(arr); // Free allocated memory
    return 0;
}
```

#### `calloc()`

- Stands for "contiguous allocation."
- Allocates memory for an array of elements and initializes all bits to zero.
- **Initialization**: Memory allocated by `calloc()` is initialized to zero.
- **Syntax**:
  ```c
  ptr = (castType*) calloc(n, size);
  ```

#### Sample Program Using `calloc()`

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *arr;
    int n = 5;

    arr = (int*) calloc(n, sizeof(int));
    if (arr == NULL) {
        printf("Memory allocation failed\n");
        return 1;
    }

    // Use the allocated array
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]); // All values will be initialized to 0
    }

    free(arr); // Free allocated memory
    return 0;
}
```

### Memory Layout of C Programs

A typical memory representation of a C program consists of several sections:

1. **Text Segment**: Contains compiled machine code; it is read-only.
2. **Initialized Data Segment**: Holds global/static variables initialized by the programmer before execution.
3. **Uninitialized Data Segment (BSS Segment)**: Contains global/static variables that are declared but not initialized.
4. **Heap**: Used for dynamic memory allocation during program execution.
5. **Stack**: Used for static memory allocation, primarily for function calls and local variables.

### Memory Leak

A memory leak occurs when a computer program incorrectly manages memory allocations, resulting in memory that is no longer needed not being released back to the system.

### Challenge

You are required to write a C program demonstrating both `malloc()` and `calloc()`. Instructions can be found in my GitHub repository [here](https://github.com/myselfbasil/Introduction-to-C-in-Linux).

---

This chapter provides a detailed examination of how memory management works in C programming, equipping readers with essential knowledge for effective programming practices within the Linux environment.
