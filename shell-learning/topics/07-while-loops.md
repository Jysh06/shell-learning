# 7. While Loops

## Overview
While loops execute a block of code repeatedly as long as a condition is true. They're useful when you don't know how many iterations you need.

---

## While Loop Syntax

```bash
while [ condition ]; do
    # Commands executed while condition is true
done
```

---

## Basic While Loop

```bash
#!/bin/bash

counter=1

while [ $counter -le 5 ]; do
    echo "Count: $counter"
    counter=$((counter + 1))
done

echo "Loop finished"
```

**Output:**
```
Count: 1
Count: 2
Count: 3
Count: 4
Count: 5
Loop finished
```

---

## While Loop with User Input

Read input until a specific value is entered.

```bash
#!/bin/bash

echo "Enter 'quit' to exit"

while true; do
    read -p "Enter command: " command
    
    if [ "$command" = "quit" ]; then
        echo "Goodbye!"
        break
    fi
    
    echo "You entered: $command"
done
```

---

## While Loop Reading File

Process each line of a file.

```bash
while IFS= read -r line; do
    echo "Line: $line"
done < filename.txt
```

### Example: Process Configuration File

```bash
#!/bin/bash

while IFS=':' read -r key value; do
    echo "Key: $key, Value: $value"
done < config.txt
```

---

## Comparison Operators in While

### Numeric Comparison

```bash
num=1

while [ $num -le 3 ]; do
    echo "Number: $num"
    ((num++))
done
```

### String Comparison

```bash
password=""

while [ -z "$password" ]; do
    read -s -p "Enter password: " password
    if [ -z "$password" ]; then
        echo "Password cannot be empty"
    fi
done

echo "Password set"
```

---

## Multiple Conditions

### Using AND (&&)

```bash
counter=1
max=5

while [ $counter -le $max ] && [ $counter -gt 0 ]; do
    echo "Count: $counter"
    ((counter++))
done
```

### Using OR (||)

```bash
while [ -z "$input" ] || [ "$input" = "retry" ]; do
    read -p "Enter something: " input
done

echo "You entered: $input"
```

---

## Until Loop

The `until` loop is the opposite of `while` - it executes while a condition is false.

```bash
counter=1

until [ $counter -gt 5 ]; do
    echo "Count: $counter"
    counter=$((counter + 1))
done

echo "Loop finished"
```

**Output:**
```
Count: 1
Count: 2
Count: 3
Count: 4
Count: 5
Loop finished
```

---

## Infinite Loop

Create a loop that runs forever (until explicitly broken).

```bash
while true; do
    read -p "Continue? (yes/no): " response
    
    if [ "$response" = "no" ]; then
        break
    fi
    
    echo "Continuing..."
done
```

---

## Break and Continue

### Break Statement

Exit the loop immediately.

```bash
count=0

while [ $count -lt 10 ]; do
    if [ $count -eq 5 ]; then
        echo "Breaking at 5"
        break
    fi
    
    echo "Count: $count"
    ((count++))
done
```

### Continue Statement

Skip the current iteration and move to the next.

```bash
count=0

while [ $count -lt 5 ]; do
    ((count++))
    
    if [ $count -eq 3 ]; then
        echo "Skipping 3"
        continue
    fi
    
    echo "Count: $count"
done
```

---

## Practical Examples

### Password Validation Loop

```bash
#!/bin/bash

attempts=0
max_attempts=3
correct_password="secret"

while [ $attempts -lt $max_attempts ]; do
    read -s -p "Enter password: " password
    echo ""
    
    if [ "$password" = "$correct_password" ]; then
        echo "Access granted!"
        break
    else
        ((attempts++))
        echo "Wrong password. Attempts remaining: $((max_attempts - attempts))"
    fi
done

if [ $attempts -eq $max_attempts ]; then
    echo "Maximum attempts exceeded. Access denied."
fi
```

### Read Configuration File

```bash
#!/bin/bash

while IFS='=' read -r key value; do
    # Skip comments and empty lines
    [[ "$key" =~ ^#.*$ ]] && continue
    [ -z "$key" ] && continue
    
    export "$key=$value"
    echo "Set: $key = $value"
done < config.txt
```

---

## Best Practices

✅ Always update the loop counter/condition  
✅ Use meaningful variable names  
✅ Quote variables: `[ "$var" = "value" ]`  
✅ Avoid infinite loops unless intentional  
✅ Use `break` to exit when needed  
✅ Use `continue` to skip iterations  
✅ Test file existence before reading  

---

## Next Topic

→ [Functions](08-functions.md)
