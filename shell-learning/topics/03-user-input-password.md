# 3. User Input & Password Handling

## Overview
Interactive scripts often need to accept user input. The `read` command is used to get input from users.

## Basic Input with read

```bash
read -p "Enter your name: " name
echo "Hello, $name!"
```

The `-p` flag displays a prompt before waiting for input.

---

## Reading Password (Silent Mode)

To read sensitive information like passwords without displaying what the user types, use the `-s` flag.

```bash
read -s -p "Enter your password: " password
echo "Password has been set"
```

The `-s` flag silences the input (doesn't echo characters as they're typed).

### Example Script

```bash
#!/bin/bash

read -s -p "Your password is: " password
echo "Password has been set: $password"
```

**Security Note:** In a real application, never display the password back. This is just for demonstration.

---

## Reading Multiple Values

```bash
read -p "Enter first name and last name: " first last
echo "Hello, $first $last!"
```

The `read` command can store input into multiple variables.

---

## Reading with Timeout

Use the `-t` flag to set a timeout (in seconds) for user input. If no input is received within the timeout, the command returns.

```bash
read -t 6 -p "Enter something in 6 seconds: " timed_out
echo "You entered: $timed_out"
```

### Example: Timeout Handling

```bash
#!/bin/bash

read -t 10 -p "Enter your name (10 seconds): " name

if [ -z "$name" ]; then
    echo "Timeout! Using default name: User"
    name="User"
fi

echo "Hello, $name!"
```

---

## Read Flags Reference

| Flag | Description |
|------|-------------|
| `-p "prompt"` | Display prompt text |
| `-s` | Silent mode (don't echo input) |
| `-t N` | Timeout after N seconds |
| `-r` | Don't interpret backslashes |
| `-n N` | Read maximum N characters |
| `-d "delimiter"` | Use custom delimiter instead of newline |

---

## Complete Example: User Registration

```bash
#!/bin/bash

echo "=== User Registration ==="

read -p "Enter username: " username
read -s -p "Enter password: " password
echo ""  # Newline after password input
read -t 5 -p "Enter email (5 seconds): " email

if [ -z "$email" ]; then
    email="not.provided@example.com"
fi

echo ""
echo "Registration Summary:"
echo "  Username: $username"
echo "  Email: $email"
```

---

## Best Practices

✅ Always use `-p` to provide clear prompts  
✅ Use `-s` for password/sensitive input  
✅ Use `-t` for interactive timeouts  
✅ Check if input is empty before using it  
✅ Provide default values for timeout scenarios  
✅ Never display passwords in output  

---

## Next Topic

→ [Conditional Statements](04-conditionals.md)
