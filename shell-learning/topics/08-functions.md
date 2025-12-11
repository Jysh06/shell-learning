# 8. Functions

## Overview
Functions are reusable blocks of code that perform specific tasks. They help organize code, reduce repetition, and make scripts more maintainable.

---

## Function Syntax

```bash
function_name() {
    # Function body
    commands
}
```

Or with the `function` keyword:

```bash
function function_name() {
    # Function body
    commands
}
```

---

## Calling a Function

```bash
#!/bin/bash

greet() {
    echo "Hello, DevOps!"
}

greet               # Call the function
greet               # Call again
```

**Output:**
```
Hello, DevOps!
Hello, DevOps!
```

---

## Functions with Parameters

Pass arguments to functions using positional parameters.

```bash
#!/bin/bash

add() {
    local num1=$1
    local num2=$2
    local sum=$((num1 + num2))
    echo "Sum: $sum"
}

add 10 20
add 5 15
```

**Output:**
```
Sum: 30
Sum: 20
```

### Parameter Reference

| Variable | Description |
|----------|-------------|
| `$1, $2, $3...` | Positional parameters |
| `$#` | Number of parameters |
| `$@` | All parameters as separate words |
| `$*` | All parameters as one word |

---

## Functions with Return Values

### Using Echo (Recommended)

```bash
get_sum() {
    local num1=$1
    local num2=$2
    echo $((num1 + num2))
}

result=$(get_sum 10 20)
echo "Result: $result"
```

**Output:** Result: 30

### Using Return Code

```bash
is_even() {
    if [ $((($1 % 2))) -eq 0 ]; then
        return 0        # Success (true)
    else
        return 1        # Failure (false)
    fi
}

if is_even 4; then
    echo "4 is even"
else
    echo "4 is odd"
fi
```

**Output:** 4 is even

---

## Variable Scope

### Local Variables

Variables declared with `local` are only accessible within the function.

```bash
counter=0           # Global

increment() {
    local counter=1 # Local to function
    ((counter++))
    echo "Inside: $counter"
}

increment
echo "Outside: $counter"
```

**Output:**
```
Inside: 2
Outside: 0
```

### Global Variables

Variables without `local` are accessible everywhere.

```bash
#!/bin/bash

name="Global"

modify() {
    name="Modified"     # Changes global variable
}

modify
echo "$name"           # Modified
```

---

## Function with All Parameters

Access all arguments passed to a function.

```bash
print_all() {
    echo "Total arguments: $#"
    echo "All arguments: $@"
    
    for arg in "$@"; do
        echo "  - $arg"
    done
}

print_all apple banana cherry
```

**Output:**
```
Total arguments: 3
All arguments: apple banana cherry
  - apple
  - banana
  - cherry
```

---

## Function Returning Multiple Values

```bash
get_file_info() {
    local file=$1
    
    # Return information about the file
    echo "$(basename "$file")"
    echo "$(wc -l < "$file")"
    echo "$(stat -c%s "$file")"
}

name=$(get_file_info "myfile.txt" | head -1)
lines=$(get_file_info "myfile.txt" | head -2 | tail -1)
size=$(get_file_info "myfile.txt" | tail -1)

echo "File: $name, Lines: $lines, Size: $size"
```

---

## Function with Error Checking

```bash
copy_file() {
    if [ $# -ne 2 ]; then
        echo "Error: Usage - copy_file <source> <destination>"
        return 1
    fi
    
    local source=$1
    local destination=$2
    
    if [ ! -f "$source" ]; then
        echo "Error: Source file not found"
        return 2
    fi
    
    cp "$source" "$destination"
    return 0
}

if copy_file "file1.txt" "file2.txt"; then
    echo "Copy successful"
else
    echo "Copy failed"
fi
```

---

## Practical Function Examples

### String Processing

```bash
reverse_string() {
    local str="$1"
    local reversed=""
    
    for ((i=${#str}-1; i>=0; i--)); do
        reversed="${reversed}${str:$i:1}"
    done
    
    echo "$reversed"
}

result=$(reverse_string "hello")
echo "Reversed: $result"  # Output: olleh
```

### Factorial Calculation

```bash
factorial() {
    local n=$1
    
    if [ $n -le 1 ]; then
        echo 1
        return 0
    fi
    
    local prev=$(factorial $((n - 1)))
    echo $((n * prev))
}

result=$(factorial 5)
echo "5! = $result"  # Output: 5! = 120
```

### File Backup Function

```bash
backup_file() {
    local file=$1
    local backup_dir="${2:-./backups}"
    local timestamp=$(date +%Y%m%d_%H%M%S)
    
    mkdir -p "$backup_dir"
    cp "$file" "$backup_dir/${file}_${timestamp}.bak"
    
    echo "Backup created: $backup_dir/${file}_${timestamp}.bak"
}

backup_file "important.txt" "./backup"
```

---

## Best Practices

✅ Use meaningful function names  
✅ Use `local` for function variables  
✅ Document function parameters in comments  
✅ Return meaningful exit codes  
✅ Quote variables: `"$var"`  
✅ Check parameters before using them  
✅ Keep functions small and focused  
✅ Use echo for returning values  

---

## Next Topic

→ [String Manipulation](09-string-manipulation.md)
