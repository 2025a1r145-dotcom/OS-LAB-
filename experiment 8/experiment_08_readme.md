# Experiment 08: Memory Allocation and Memory Usage in C

## Aim

To study and demonstrate dynamic memory allocation (`malloc`), physical page commitment, and memory deallocation (`free`) in C, as well as observing real-time system memory usage in Linux.

## Prerequisites

* **Compiler:** GCC (`gcc`)
* **OS:** Linux (Ubuntu or similar distribution)
* **Monitoring Tools (Optional):** `free -h`, `top`, or `htop`

## Program: Dynamic Memory Allocation in C

This program accepts a memory size in megabytes (MB) via command-line arguments, dynamically allocates the requested memory on the heap, touches each 4 KB memory page to force physical RAM allocation (avoiding lazy allocation), pauses for observation, and safely releases the memory.

```c
// Experiment 8: Memory Allocation and Memory Usage in C

#include <stdio.h>
#include <stdlib.h>

int main(int argc, char *argv[]) {
    if (argc != 2) {
        printf("Usage: %s <memory_in_MB>\n", argv[0]);
        return 1;
    }

    int mb = atoi(argv[1]);

    if (mb <= 0) {
        printf("Please enter a positive memory size.\n");
        return 1;
    }

    size_t size = (size_t)mb * 1024 * 1024;

    char *ptr = (char *)malloc(size);

    if (ptr == NULL) {
        printf("Memory allocation failed.\n");
        return 1;
    }

    // Touch each 4 KB page so the OS commits physical memory
    for (size_t i = 0; i < size; i += 4096) {
        ptr[i] = 0;
    }

    printf("%d MB memory allocated successfully.\n", mb);

    printf("Press Enter to release memory...");
    getchar();
    getchar();

    free(ptr);

    printf("Memory released successfully.\n");

    return 0;
}
```

## Compilation and Execution

1. **Save the source code** as `memory_alloc.c`.
2. **Compile the program** using GCC:
   ```bash
   gcc memory_alloc.c -o memory_alloc
   ```
3. **Run the executable** by passing the desired memory size in MB (e.g., `500` MB):
   ```bash
   ./memory_alloc 500
   ```
4. **Monitor Memory Usage:** While the program is paused at `"Press Enter to release memory..."`, open a second terminal and run `free -h` or `top` to observe the increase in used RAM.
5. **Release Memory:** Return to the program terminal and press `Enter` to call `free(ptr)` and release the allocated memory back to the OS.

## Key Concepts Demonstrated

* **Command-Line Arguments (`argc`, `argv`):** Reading user input directly at program launch.
* **Heap Allocation (`malloc`):** Allocating a contiguous block of memory dynamically at runtime.
* **Page Touching (`4096` bytes):** Writing to every 4 KB page boundary ensures the Linux kernel maps physical frames to the virtual address space rather than relying on demand paging.
* **Memory Deallocation (`free`):** Preventing memory leaks by explicitly freeing allocated heap space before program termination.

## Result

Dynamic memory allocation, physical page commitment, and memory deallocation in C were successfully implemented, executed, and verified in a Linux environment.