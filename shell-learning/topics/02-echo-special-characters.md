# 2. Echo Behavior & Special Characters

## Overview
The `echo` command displays text and variables. Understanding how quotes work is essential for proper output.

## Echo with Double Quotes

Double quotes allow variable expansion and interpretation of escape sequences.

```bash
variable="Hello World"
echo "$variable"
# Output: Hello World
```

Variables inside double quotes are replaced with their values.

---

## Echo with Single Quotes

Single quotes preserve everything literally - no variable expansion occurs.

```bash
variable="Hello World"
echo '$variable'
# Output: $variable
```

---

## Echo without Quotes

Unquoted variables work but can cause issues with spaces.

```bash
variable="Hello World"
echo $variable
# Output: Hello World (but risky with spaces)
```

---

## Special Characters

### Dollar Sign ($)

To print a literal dollar sign, escape it with a backslash.

```bash
special_char="\$"
echo "Price is $special_char100"
# Output: Price is $100
```

### Backslash (\)

The backslash escapes special characters, preventing their interpretation.

```bash
echo "He said \"Hello\""
# Output: He said "Hello"

echo "C:\\Users\\Name"
# Output: C:\Users\Name
```

---

## Escape Sequences with -e Flag

Use `echo -e` to interpret escape sequences.

| Escape | Description |
|--------|-------------|
| `\n` | Newline |
| `\t` | Tab |
| `\\` | Backslash |
| `\"` | Double quote |
| `\'` | Single quote |
| `\$` | Dollar sign |

### Examples

```bash
echo -e "Line 1\nLine 2"
# Output:
# Line 1
# Line 2

echo -e "Col1\tCol2\tCol3"
# Output: Col1    Col2    Col3
```

---

## Complete Echo Examples

```bash
#!/bin/bash

variable="Hello World"

echo "$variable"           # Prints: Hello World
echo '$variable'           # Prints: $variable (literal)
echo $variable             # Prints: Hello World (unquoted)
echo "both '$variable'"    # Prints: both 'Hello World'

special_char="\$"
echo "special char - $special_char"
# Output: special char - $
```

---

## Best Practices

✅ Always use double quotes for variables: `"$var"`  
✅ Use single quotes for literal strings  
✅ Escape special characters when needed  
✅ Use `echo -e` for escape sequences  
✅ Be consistent with quoting style

---

## Next Topic

→ [User Input & Password Handling](03-user-input-password.md)
