# 4. Conditional Statements

## Overview
Conditional statements allow you to execute different code based on different conditions.

---

## If Statement

The simplest form of conditional logic.

```bash
if [ condition ]; then
    # Commands executed if condition is true
fi
```

### Example

```bash
num=10

if [ $num -gt 5 ]; then
    echo "Number is greater than 5"
fi
```

---

## If-Else Statement

Execute one block if condition is true, another if false.

```bash
if [ condition ]; then
    # True condition
else
    # False condition
fi
```

### Example

```bash
num=10

if [ $num -gt 10 ]; then
    echo "Number is greater than 10"
else
    echo "Number is not greater than 10"
fi
```

---

## If-Elif-Else Statement

Test multiple conditions in sequence.

```bash
num=10

if [ $num -gt 10 ]; then
    echo "Number is greater than 10"
elif [ $num -eq 10 ]; then
    echo "Number is equal to 10"
else
    echo "Number is less than 10"
fi
```

---

## Comparison Operators

### Numeric Comparison

| Operator | Description |
|----------|-------------|
| `-eq` | Equal to |
| `-ne` | Not equal to |
| `-lt` | Less than |
| `-le` | Less than or equal |
| `-gt` | Greater than |
| `-ge` | Greater than or equal |

### Examples

```bash
a=10
b=20

[ $a -eq $b ]   # False (10 is not equal to 20)
[ $a -ne $b ]   # True (10 is not equal to 20)
[ $a -lt $b ]   # True (10 is less than 20)
[ $a -gt $b ]   # False (10 is not greater than 20)
```

---

## String Comparison

### String Operators

| Operator | Description |
|----------|-------------|
| `=` | Equal |
| `!=` | Not equal |
| `-z` | String is empty |
| `-n` | String is not empty |

### Examples

```bash
str1="hello"
str2="world"

if [ "$str1" = "$str2" ]; then
    echo "Strings are equal"
else
    echo "Strings are different"
fi

if [ -z "$str1" ]; then
    echo "String is empty"
fi

if [ -n "$str1" ]; then
    echo "String is not empty"
fi
```

---

## File Tests

Test file properties and existence.

| Test | Description |
|------|-------------|
| `-f` | File exists and is a regular file |
| `-d` | File exists and is a directory |
| `-e` | File exists (any type) |
| `-r` | File is readable |
| `-w` | File is writable |
| `-x` | File is executable |

### Examples

```bash
if [ -f "$filename" ]; then
    echo "File exists"
fi

if [ -d "$dirname" ]; then
    echo "Directory exists"
fi

if [ -r "$filename" ]; then
    echo "File is readable"
fi
```

---

## Logical Operators

### AND (&&)

True if both conditions are true.

```bash
age=25

if [ $age -ge 18 ] && [ $age -le 65 ]; then
    echo "Working age"
fi
```

### OR (||)

True if at least one condition is true.

```bash
score=45

if [ $score -lt 50 ] || [ $score -gt 90 ]; then
    echo "Extreme score"
fi
```

### NOT (!)

Inverts the condition.

```bash
if [ ! -f "$filename" ]; then
    echo "File does not exist"
fi
```

---

## Complete Example

```bash
#!/bin/bash

num=10

if [ $num -gt 10 ]; then
    echo "Number is greater than 10"
elif [ $num -eq 10 ]; then
    echo "Number is equal to 10"
else
    echo "Number is less than 10"
fi
```

---

## Best Practices

✅ Always quote variables: `[ "$var" = "value" ]`  
✅ Use spaces around operators: `[ $a -gt $b ]`  
✅ Use `-eq` for numeric comparison  
✅ Use `=` for string comparison  
✅ Use `-z` and `-n` for string checks  

---

## Next Topic

→ [Case/Switch Statements](05-case-switch.md)
