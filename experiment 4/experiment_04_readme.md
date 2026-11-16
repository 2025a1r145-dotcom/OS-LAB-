# Experiment 04: Process Management and Text Editors in Linux

## Aim

To study and demonstrate Linux process management commands (`ps`, `top`, `kill`, `pstree`, background execution) and basic operations in `vi` and `nano` text editors.

## Programs & Editor Operations

### Program 1: Display Running Processes

Demonstrates viewing active processes for the current shell (`ps`) and all running system processes (`ps -ef`).

```bash
#!/bin/bash

echo "Displaying running processes:"
ps

echo ""
echo "Displaying all processes:"
ps -ef
```

### Program 2: Display Process Information

Demonstrates retrieving the current shell Process ID (`$$`), active user (`whoami`), and a snapshot of top resource-consuming processes (`top`).

```bash
#!/bin/bash

echo "Current shell process ID:"
echo $$

echo ""
echo "Current user:"
whoami

echo ""
echo "Running processes:"
top -b -n 1 | head -n 10
```

### Program 3: Run a Process in the Background

Demonstrates running a task in the background (`&`), capturing its PID (`$!`), monitoring its status, and waiting for completion (`wait`).

```bash
#!/bin/bash

echo "Starting a background process..."

sleep 30 &

PID=$!

echo "Background process started."
echo "Process ID: $PID"

echo ""
echo "Checking the process:"
ps -p "$PID"

wait "$PID"

echo "Background process completed."
```

### Program 4: Terminate a Process

Demonstrates starting a background process and terminating it programmatically using the `kill` command.

```bash
#!/bin/bash

sleep 100 &

PID=$!

echo "Started sleep process with PID: $PID"

sleep 2

if kill "$PID" 2>/dev/null; then
    echo "Termination signal sent to process $PID."
else
    echo "Process could not be terminated."
fi
```

### Program 5: `vi` Editor Commands

**Open or create a file:**
```bash
vi sample.txt
```

**Common commands inside `vi`:**

| Command | Action |
| :--- | :--- |
| `i` | Enter insert mode |
| `Esc` | Exit insert mode (return to command mode) |
| `:w` | Save the file |
| `:q` | Quit the editor |
| `:wq` | Save and quit |
| `:q!` | Quit without saving |

### Program 6: `nano` Editor Commands

**Open or create a file:**
```bash
nano sample.txt
```

**Common shortcuts inside `nano`:**

| Shortcut | Action |
| :--- | :--- |
| `Ctrl + O` | Save the file |
| `Enter` | Confirm the filename |
| `Ctrl + X` | Exit the editor |
| `Ctrl + W` | Search for text |
| `Ctrl + K` | Cut a line |
| `Ctrl + U` | Paste a line |

### Program 7: Display Process Tree

Demonstrates displaying running processes in a hierarchical tree format using `pstree`.

```bash
#!/bin/bash

echo "Displaying process tree:"
pstree
```

> **Note:** If `pstree` is not installed on your system, install it using:
> ```bash
> sudo apt install psmisc
> ```

## Result

Process management commands and basic operations of `vi` and `nano` text editors were successfully studied and demonstrated in Linux.