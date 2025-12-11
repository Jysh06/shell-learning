# 5. Case/Switch Statements

## Overview
The `case` statement is used when you need to test a variable against multiple values. It's cleaner than multiple `if-elif-else` statements.

---

## Case Statement Syntax

```bash
case variable in
    pattern1)
        # Commands if variable matches pattern1
        ;;
    pattern2)
        # Commands if variable matches pattern2
        ;;
    *)
        # Commands if variable doesn't match any pattern
        ;;
esac
```

**Important:** Each case must end with `;;`

---

## Basic Example

```bash
#!/bin/bash

fruit="apple"

case $fruit in
    "apple")
        echo "It is an apple"
        ;;
    "banana")
        echo "It is a banana"
        ;;
    "mango")
        echo "It is a mango"
        ;;
    *)
        echo "Unknown fruit"
        ;;
esac
```

**Output:** It is an apple

---

## Multiple Patterns

You can match multiple patterns for the same action using the pipe `|` operator.

```bash
#!/bin/bash

day="Saturday"

case $day in
    "Monday"|"Tuesday"|"Wednesday"|"Thursday"|"Friday")
        echo "It's a weekday"
        ;;
    "Saturday"|"Sunday")
        echo "It's a weekend"
        ;;
    *)
        echo "Unknown day"
        ;;
esac
```

**Output:** It's a weekend

---

## Pattern Matching with Wildcards

You can use wildcards in patterns.

```bash
#!/bin/bash

filename="document.pdf"

case $filename in
    *.txt)
        echo "Text file"
        ;;
    *.pdf)
        echo "PDF file"
        ;;
    *.jpg|*.png|*.gif)
        echo "Image file"
        ;;
    *)
        echo "Unknown file type"
        ;;
esac
```

**Output:** PDF file

---

## Case with User Input

```bash
#!/bin/bash

read -p "Choose an option (1-3): " choice

case $choice in
    1)
        echo "You selected option 1"
        ;;
    2)
        echo "You selected option 2"
        ;;
    3)
        echo "You selected option 3"
        ;;
    *)
        echo "Invalid choice"
        ;;
esac
```

---

## Case vs If-Elif-Else

### Using If-Elif-Else (Verbose)

```bash
if [ "$fruit" = "apple" ]; then
    echo "Apple"
elif [ "$fruit" = "banana" ]; then
    echo "Banana"
elif [ "$fruit" = "mango" ]; then
    echo "Mango"
else
    echo "Unknown"
fi
```

### Using Case (Cleaner)

```bash
case $fruit in
    "apple")
        echo "Apple"
        ;;
    "banana")
        echo "Banana"
        ;;
    "mango")
        echo "Mango"
        ;;
    *)
        echo "Unknown"
        ;;
esac
```

---

## Default Case (Wildcard)

The `*` pattern matches anything and acts as the default case.

```bash
case $value in
    10)
        echo "Value is 10"
        ;;
    20)
        echo "Value is 20"
        ;;
    *)
        echo "Value is something else"
        ;;
esac
```

---

## Complete Example: Menu System

```bash
#!/bin/bash

echo "=== Simple Menu ==="
echo "1. View files"
echo "2. Create file"
echo "3. Delete file"
echo "4. Exit"
echo ""

read -p "Select an option: " option

case $option in
    1)
        echo "Listing files..."
        ls -la
        ;;
    2)
        read -p "Enter filename: " filename
        touch "$filename"
        echo "File created: $filename"
        ;;
    3)
        read -p "Enter filename to delete: " filename
        rm "$filename"
        echo "File deleted"
        ;;
    4)
        echo "Exiting..."
        exit 0
        ;;
    *)
        echo "Invalid option"
        ;;
esac
```

---

## Best Practices

✅ Always use `;;` to end each case  
✅ Use `*)` as the default case  
✅ Quote variables: `case "$var" in`  
✅ Use case for multiple options instead of if-elif-else  
✅ Use `|` to combine multiple patterns  
✅ Indent code for readability  

---

## Next Topic

→ [For Loops](06-for-loops.md)
