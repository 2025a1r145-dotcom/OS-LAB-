# Experiment 09: CPU-Bound and I/O-Bound Processes

## Aim

To study, implement, and observe the behavior of CPU-bound and I/O-bound processes in C, and to monitor their resource utilization and memory maps using Linux process management tools (`top` and `pmap`).

## Prerequisites

* **OS:** Linux (Ubuntu or similar distribution)
* **Compiler:** GCC (`gcc`)
* **Monitoring Tools:** `top`, `pmap` (from the `procps` package)

## Programs

### 1. CPU-Bound C Program (`cpu_bound.c`)

Performs heavy arithmetic iterations (`100,000,000` loop cycles) using the `volatile` keyword to prevent compiler loop optimization, keeping the CPU core actively engaged.

```c
#include <stdio.h>

int main(void) {
    volatile unsigned long long sum = 0;

    for (unsigned long long i = 1; i <= 100000000ULL; i++) {
        sum += i;
    }

    printf("CPU Bound Process\n");
    printf("Sum = %llu\n", sum);

    return 0;
}
```

### 2. I/O-Bound C Program (`io_bound.c`)

Performs repeated file write operations (`100,000` lines) to `output.txt`, spending a significant portion of its lifecycle waiting on disk/storage subsystem I/O operations.

```c
#include <stdio.h>

int main(void) {
    FILE *fp = fopen("output.txt", "w");

    if (fp == NULL) {
        perror("fopen");
        return 1;
    }

    for (int i = 1; i <= 100000; i++) {
        fprintf(fp, "Writing data: %d\n", i);
    }

    fclose(fp);

    printf("I/O Bound Process Completed\n");
    return 0;
}
```

## Compilation and Execution

### 1. Compile the Programs

```bash
gcc cpu_bound.c -o cpu
gcc io_bound.c -o io
```

### 2. Run the Executables

* **Run the CPU-bound program:**
  ```bash
  ./cpu
  ```
* **Run the I/O-bound program:**
  ```bash
  ./io
  ```

## Process Monitoring & Memory Inspection

1. **Monitor Real-Time CPU and Resource Usage:**
   Open a separate terminal window while running the programs to observe CPU percentage (`%CPU`) and process state (`R` for running vs. `D`/`S` for waiting/sleeping):
   ```bash
   top
   ```

2. **View Process Memory Map:**
   Find the Process ID (`PID`) of the running process (via `top` or `ps`) and inspect its virtual memory layout:
   ```bash
   pmap <PID>
   ```
   *(Replace `<PID>` with the actual process ID shown by the system.)*

## Key Notes & Observations

* **CPU-Bound Behavior:** The `cpu_bound.c` program performs repeated arithmetic calculations in user space, maximizing CPU core utilization until completion.
* **I/O-Bound Behavior:** The `io_bound.c` program repeatedly writes data to disk, relying on system calls and storage buffers.
* **Hardware Variance:** The exact `%CPU` utilization and execution duration observed in `top` will vary depending on your system's CPU clock speed, storage speed (SSD vs. HDD), and how quickly each program finishes.

## Result

CPU-bound and I/O-bound processes were successfully implemented in C, executed, and monitored using `top` and `pmap` in a Linux environment.