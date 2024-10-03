# Introduction to C in Linux

## Chapter 2 Exercise: 

The compilation process of a C program in Linux involves several key stages: preprocessing, compiling, assembling, linking, and loading. Each stage transforms the code into a format that the machine can execute. Below is a detailed explanation of each step using the provided C code as an example.

### C Code Example Question:

```c
#include <stdio.h>

// Function prototype
unsigned long long factorial(int n);

int main() {
    int number;
    unsigned long long result;

    // Prompt the user for input
    printf("Enter a positive integer: ");
    scanf("%d", &number);

    // Check for negative input
    if (number < 0) {
        printf("Error: Factorial is not defined for negative numbers.\n");
        return 1; // Return with an error code
    }

    // Calculate the factorial
    result = factorial(number);

    // Display the result
    printf("Factorial of %d = %llu\n", number, result);
    
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

### 1. Preprocessing

**What Happens**: The preprocessor handles directives that begin with `#`, such as `#include` and `#define`. It removes comments and expands macros.

**Commands**:
- To preprocess the code and generate an intermediate file (`.i`):
  ```bash
  gcc -E factorial.c -o factorial.i
  ```

**Output**: The `factorial.i` file contains the expanded source code with all header file contents included and comments removed.

### 2. Compiling

**What Happens**: The compiler translates the preprocessed code into assembly language specific to the target architecture.

**Commands**:
- To compile the preprocessed file into assembly language (`.s`):
  ```bash
  gcc -S factorial.i -o factorial.s
  ```

**Output**: The `factorial.s` file contains assembly instructions corresponding to the C code.

### 3. Assembling

**What Happens**: The assembler converts the assembly language code into machine code, producing an object file (`.o`).

**Commands**:
- To assemble the assembly file into an object file:
  ```bash
  gcc -c factorial.s -o factorial.o
  ```

**Output**: The `factorial.o` file contains binary machine code that is not directly human-readable.

### 4. Linking

**What Happens**: The linker combines one or more object files into a single executable. It resolves references to external functions (like those from libraries).

**Commands**:
- To link the object file and create an executable:
  ```bash
  gcc factorial.o -o factorial
  ```

**Output**: The executable file named `factorial` is created, which can be run directly.

### 5. Loading

After linking, when you run your program, the loader is responsible for loading the executable into memory and preparing it for execution.

**Command to Run Executable**:
```bash
./factorial
```

### Summary of Commands

Here’s a summary of all commands used in this process:

| Step         | Command                                      | Output File           |
|--------------|----------------------------------------------|-----------------------|
| Preprocessing| `gcc -E factorial.c -o factorial.i`         | `factorial.i`         |
| Compiling    | `gcc -S factorial.i -o factorial.s`        | `factorial.s`         |
| Assembling   | `gcc -c factorial.s -o factorial.o`        | `factorial.o`         |
| Linking      | `gcc factorial.o -o factorial`              | `factorial`           |
| Execution    | `./factorial`                               | Program output on console |

### Conclusion

Understanding each step of the compilation process in C on Linux helps developers optimize their code and troubleshoot issues effectively. Each stage plays a crucial role in transforming high-level source code into an executable binary that can be run on a computer. By manually executing these steps, programmers gain deeper insights into how their code is processed and executed by the system.