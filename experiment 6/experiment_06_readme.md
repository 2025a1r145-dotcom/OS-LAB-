# Experiment 06: User Information, Line Extraction, and Text Processing in Linux

## Aim

To study and demonstrate user information commands, line extraction, text searching, word counting, sorting, and text replacement using Bash shell scripts in Linux.

## Programs

### Program 1: Display Current User Information

Demonstrates retrieving the current username (`whoami`), user/group IDs (`id`), active login sessions (`who`), and the system date and time (`date`).

```bash
#!/bin/bash

echo "Current Username:"
whoami

echo ""
echo "User ID and Group ID:"
id

echo ""
echo "Current Login Sessions:"
who

echo ""
echo "Current Date and Time:"
date
```

### Program 2: Display User Login History

Demonstrates viewing the most recent login records (`last`) alongside the active user (`whoami`).

```bash
#!/bin/bash

echo "Recent Login History:"
last -n 5

echo ""
echo "Current User:"
whoami
```

### Program 3: Count Lines, Words, and Characters

Demonstrates creating a text file and counting its lines (`wc -l`), words (`wc -w`), and characters (`wc -m`).

```bash
#!/bin/bash

filename="sample.txt"

cat > "$filename" <<EOF
Linux is an operating system.
Shell scripting is useful.
Text processing is important.
EOF

echo "File Contents:"
cat "$filename"

echo ""
echo "Number of Lines:"
wc -l < "$filename"

echo "Number of Words:"
wc -w < "$filename"

echo "Number of Characters:"
wc -m < "$filename"
```

### Program 4: Extract a Specific Line

Demonstrates extracting individual lines by line number using `sed -n`.

```bash
#!/bin/bash

filename="sample.txt"

echo "First line:"
sed -n '1p' "$filename"

echo ""
echo "Second line:"
sed -n '2p' "$filename"

echo ""
echo "Third line:"
sed -n '3p' "$filename"
```

### Program 5: Search for a Word in a File

Demonstrates searching for a specific pattern with line numbers (`grep -n`) and handling the search result conditionally.

```bash
#!/bin/bash

filename="sample.txt"
search_word="Linux"

echo "Searching for the word: $search_word"

if grep -n "$search_word" "$filename"; then
    echo "Search completed."
else
    echo "Word not found."
fi
```

### Program 6: Replace Text Using `sed`

Demonstrates global string substitution within a file using `sed`.

```bash
#!/bin/bash

filename="sample.txt"

echo "Original Text:"
cat "$filename"

echo ""
echo "Modified Text:"
sed 's/Linux/Ubuntu/g' "$filename"
```

### Program 7: Display Unique Lines

Demonstrates sorting lines and removing duplicate entries using `sort -u`.

```bash
#!/bin/bash

cat > duplicate.txt <<EOF
Apple
Banana
Apple
Mango
Banana
Orange
EOF

echo "Original Lines:"
cat duplicate.txt

echo ""
echo "Unique Lines:"
sort -u duplicate.txt
```

### Program 8: Sort Text File Contents

Demonstrates sorting the lines of a text file alphabetically using `sort`.

```bash
#!/bin/bash

filename="fruits.txt"

cat > "$filename" <<EOF
Mango
Apple
Orange
Banana
EOF

echo "Original File:"
cat "$filename"

echo ""
echo "Sorted File:"
sort "$filename"
```

## Result

User information commands, line extraction, text searching, word counting, sorting, and text replacement using Linux commands were successfully studied and demonstrated.