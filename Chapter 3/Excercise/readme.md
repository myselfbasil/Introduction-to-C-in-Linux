# Exercise Overview for Chapter 3: Memory Management in C

## Challenge: Implementing Dynamic Memory Allocation

In this exercise, you will write a C program that demonstrates the use of both `malloc()` and `calloc()` functions for dynamic memory allocation. This challenge will help reinforce your understanding of memory management concepts introduced in Chapter 3.

### Objectives

1. **Use `malloc()`** to allocate memory for an array of integers.
2. **Use `calloc()`** to allocate memory for an array of integers and initialize it to zero.
3. **Print the values stored in both arrays** to verify correct allocation and initialization.
4. **Free the allocated memory** after use to prevent memory leaks.

### Instructions

1. **Create a new C file** named `memory_management.c`.
2. **Include necessary headers**:
   - Use `#include <stdio.h>` for input/output functions.
   - Use `#include <stdlib.h>` for memory allocation functions.

3. **Write the main function**:
   - Prompt the user to enter the number of elements they want to store in the arrays.
   - Allocate memory for an integer array using `malloc()`.
   - Allocate memory for another integer array using `calloc()`.
   - Check if the memory allocation was successful. If not, print an error message and exit the program.
   - Fill the array allocated by `malloc()` with values from 1 to n (where n is the number of elements).
   - Print the values of both arrays.
   - Free the allocated memory before exiting.

### Sample Code Structure

Here’s a basic outline to help you get started:

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
        printf("Memory allocation using malloc failed\n");
        return 1; // Exit if allocation fails
    }

    // Allocate memory using calloc
    int *callocArray = (int *)calloc(n, sizeof(int));
    if (callocArray == NULL) {
        printf("Memory allocation using calloc failed\n");
        free(mallocArray); // Free previously allocated memory
        return 1; // Exit if allocation fails
    }

    // Fill mallocArray with values
    for (int i = 0; i < n; i++) {
        mallocArray[i] = i + 1; // Assign values 1 to n
    }

    // Print values from mallocArray
    printf("Values in mallocArray: ");
    for (int i = 0; i < n; i++) {
        printf("%d ", mallocArray[i]);
    }
    printf("\n");

    // Print values from callocArray (should be all zeros)
    printf("Values in callocArray: ");
    for (int i = 0; i < n; i++) {
        printf("%d ", callocArray[i]);
    }
    printf("\n");

    // Free allocated memory
    free(mallocArray);
    free(callocArray);

    return 0;
}
```

### Submission

Once you have completed the exercise, compile your program using GCC:

```bash
gcc -o memory_management memory_management.c
```

Run your program:

```bash
./memory_management
```

Make sure to test your program with different input values to ensure it works correctly.

### Additional Resources

For more details and examples, refer to the GitHub repository linked in Chapter 3:

[GitHub Repository](https://github.com/myselfbasil/Introduction-to-C-in-Linux)

---

This exercise aims to solidify your understanding of dynamic memory allocation in C and ensure you can effectively manage memory within your programs. Happy coding!
