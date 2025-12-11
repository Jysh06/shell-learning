# 6. For Loops

## Overview
For loops are used to iterate over a sequence of values. They're perfect for processing lists, files, or ranges.

---

## Basic For Loop Syntax

```bash
for variable in list; do
    # Commands using $variable
done
```

---

## Numeric Loop with Range

Loop through numbers using the `{start..end}` syntax.

```bash
for i in {1..5}; do
    echo "Number: $i"
done
```

**Output:**
```
Number: 1
Number: 2
Number: 3
Number: 4
Number: 5
```

### Range with Step

```bash
for i in {1..10..2}; do
    echo "Odd: $i"
done
```

**Output:**
```
Odd: 1
Odd: 3
Odd: 5
Odd: 7
Odd: 9
```

---

## Loop Through List

```bash
for i in 1 2 3 4 5; do
    echo "numbers $i"
done
```

---

## Loop Through Array

```bash
fruits=("apple" "banana" "cherry")

for fruit in "${fruits[@]}"; do
    echo "Fruit: $fruit"
done
```

**Output:**
```
Fruit: apple
Fruit: banana
Fruit: cherry
```

### Using Named Array

```bash
names=("John" "Jane" "Bob")

for name in "${names[@]}"; do
    echo "Name: $name"
done
```

---

## C-Style For Loop

Use traditional C-style syntax for more control.

```bash
for ((i=1; i<=5; i++)); do
    echo "Count: $i"
done
```

### With Decrements

```bash
for ((i=5; i>=1; i--)); do
    echo "Countdown: $i"
done
```

---

## Loop Through Files

Process all files in a directory.

```bash
for file in *.txt; do
    echo "Processing: $file"
done
```

### With Full Path

```bash
for file in /path/to/files/*; do
    if [ -f "$file" ]; then
        echo "File: $file"
    fi
done
```

---

## Loop Through Command Output

Iterate over the output of a command.

```bash
for line in $(cat filename.txt); do
    echo "Line: $line"
done
```

---

## Nested Loops

```bash
for i in {1..3}; do
    for j in {1..3}; do
        echo "$i-$j"
    done
done
```

**Output:**
```
1-1
1-2
1-3
2-1
2-2
2-3
3-1
3-2
3-3
```

---

## Break and Continue

### Break (Exit Loop)

```bash
for i in {1..10}; do
    if [ $i -eq 5 ]; then
        echo "Stopping at 5"
        break
    fi
    echo "Number: $i"
done
```

### Continue (Skip Iteration)

```bash
for i in {1..5}; do
    if [ $i -eq 3 ]; then
        echo "Skipping 3"
        continue
    fi
    echo "Number: $i"
done
```

**Output:**
```
Number: 1
Number: 2
Skipping 3
Number: 4
Number: 5
```

---

## Practical Examples

### Count Files by Type

```bash
#!/bin/bash

echo "=== File Type Summary ==="

for file in *; do
    case $file in
        *.txt)
            echo "Text: $file"
            ;;
        *.sh)
            echo "Script: $file"
            ;;
        *.md)
            echo "Markdown: $file"
            ;;
    esac
done
```

### Process Array with Index

```bash
#!/bin/bash

fruits=("apple" "banana" "cherry")

for ((i=0; i<${#fruits[@]}; i++)); do
    echo "[$i] ${fruits[$i]}"
done
```

**Output:**
```
[0] apple
[1] banana
[2] cherry
```

---

## Best Practices

✅ Quote array variables: `"${array[@]}"`  
✅ Quote file variables: `"$file"`  
✅ Use meaningful loop variable names  
✅ Be careful with spaces in lists  
✅ Use C-style for numerical operations  
✅ Use for-in for iterating lists/arrays  

---

## Next Topic

→ [While Loops](07-while-loops.md)
