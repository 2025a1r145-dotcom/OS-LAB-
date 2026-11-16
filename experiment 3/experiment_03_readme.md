# Experiment 03: I/O Redirection, Pipes, and `sed` Commands

## Aim
To study and demonstrate Input/Output (I/O) redirection, pipes (`|`), and stream editing (`sed`) commands using Bash shell scripts in Linux.

---

## Programs

### Program 1: Input and Output Redirection
Demonstrates overwriting (`>`) and appending (`>>`) standard output to a file.

```bash
#!/bin/bash

echo "Hello, Operating System" > output.txt
echo "Welcome to Linux" >> output.txt

echo "Contents of output.txt:"
cat output.txt

echo "Program executed successfully."
```

---

### Program 2: Using Pipes
Demonstrates chaining commands together using pipes (`|`) to count lines and filter directory entries.

```bash
#!/bin/bash

echo "Displaying all files and directories:"
ls -l

echo ""
echo "Counting the number of lines:"
ls -l | wc -l

echo ""
echo "Displaying only directory names:"
ls -l | grep "^d"
```

---

### Program 3: Using `sed` Command
Demonstrates global text substitution using `sed`.

```bash
#!/bin/bash

echo "Linux is easy to learn" > sample.txt

echo "Original text:"
cat sample.txt

echo ""
echo "Replacing Linux with Ubuntu:"
sed 's/Linux/Ubuntu/g' sample.txt
```

---

### Program 4: Save Modified Text to a New File
Demonstrates combining `sed` with output redirection (`>`) to save modified text into a new file.

```bash
#!/bin/bash

echo "Operating System is an important subject" > input.txt

echo "Original file:"
cat input.txt

sed 's/Operating System/OS/g' input.txt > output.txt

echo ""
echo "Modified file:"
cat output.txt
```

---

### Program 5: Delete a Line Using `sed`
Demonstrates creating a multi-line file using a Here Document (`<<EOF`) and deleting a specific line using `sed`.

```bash
#!/bin/bash

cat > sample.txt <<EOF
First line
Second line
Third line
Fourth line
EOF

echo "Original file:"
cat sample.txt

echo ""
echo "After deleting the second line:"
sed '2d' sample.txt
```

---

### Program 6: Display Selected Lines Using `sed`
Demonstrates suppressing automatic output (`-n`) and printing only a specific line (`p`) using `sed`.

```bash
#!/bin/bash

echo "First line
Second line
Third line
Fourth line" > lines.txt

echo "Displaying the second line:"
sed -n '2p' lines.txt
```

---

### Program 7: Count Words Using Pipe
Demonstrates piping file content into `wc -w` to count the total number of words.

```bash
#!/bin/bash

echo "Linux is easy to learn" > words.txt

echo "Original text:"
cat words.txt

echo ""
echo "Number of words:"
cat words.txt | wc -w
```

---

## Result
I/O redirection, pipes, and `sed` commands were successfully studied and demonstrated using Bash shell scripts.