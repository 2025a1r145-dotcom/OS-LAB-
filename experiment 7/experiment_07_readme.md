# Experiment 07: String Operations Using Shell Script and C Program

## Aim

To implement string operations—specifically substring extraction and finding string length—using both a Bash shell script and a C program, and to compare their execution times using the `time` command.

## Prerequisites

* **OS:** Linux (Ubuntu or similar distribution)
* **Shell:** Bash (`/bin/bash`)
* **Compiler:** GCC (`gcc`)

## Programs

### 1. Shell Script to Extract Substring and Find Length (`substring.sh`)

Uses `cut` (1-based character indexing) to extract the specified substring and Bash parameter expansion (`${#str}`) to determine the string length.

```bash
#!/bin/bash

echo "Enter a string:"
read str

echo "Enter starting position:"
read start

echo "Enter substring length:"
read len

echo "Substring:"
echo "$str" | cut -c${start}-$((start+len-1))

echo "Length of string: ${#str}"
```

### 2. C Program to Extract Substring and Find Length (`substring.c`)

Uses array indexing (0-based indexing) to iterate through and print the requested substring characters, and `strlen()` from `<string.h>` to calculate the total length.

```c
#include <stdio.h>
#include <string.h>

int main() {
    char str[100];
    int start, len, i;

    printf("Enter a string: ");
    scanf("%99s", str);

    printf("Enter starting position (0-based): ");
    scanf("%d", &start);

    printf("Enter substring length: ");
    scanf("%d", &len);

    printf("Substring: ");

    for (i = start; i < start + len && str[i] != '\0'; i++) {
        if (start >= 0 && len >= 0)
            printf("%c", str[i]);
    }

    printf("\nString length: %lu\n",
           (unsigned long)strlen(str));

    return 0;
}
```

## Execution and Performance Comparison

Use the Linux `time` utility to measure and compare the execution speed (`real`, `user`, and `sys` time) of the interpreted shell script against the compiled C binary.

### 1. Run and Time the Shell Script

```bash
time bash substring.sh
```

### 2. Compile, Run, and Time the C Program

```bash
gcc substring.c -o substring
time ./substring
```

## Key Observations

* **Indexing Difference:** The `cut` command in the shell script uses **1-based indexing**, whereas character arrays in C use **0-based indexing**.
* **Execution Speed:** The compiled C program executes faster in terms of CPU/system overhead (`user` and `sys` time) because it runs natively as machine code without spawning external sub-processes (like `echo` and `cut`) as the Bash script does.

## Result

String length calculation and substring extraction were successfully implemented using both a Bash shell script and a C program, and their running times were compared using the `time` command.