# Shell Scripting Topics Index

A comprehensive guide to shell scripting fundamentals. Each topic is organized in a separate file for better learning and reference.

---

## 📚 Topics Guide

### 1. [Variables & Basic Operations](01-variables-operations.md)
Learn how to create and use variables, perform string concatenation, calculate string length, and work with arithmetic operations.

### 2. [Echo Behavior & Special Characters](02-echo-special-characters.md)
Understand how to display output with proper quoting, escape special characters, and handle escape sequences.

### 3. [User Input & Password Handling](03-user-input-password.md)
Master reading user input with the `read` command, handling password input securely, and setting timeouts.

### 4. [Conditional Statements](04-conditionals.md)
Explore if-else statements, comparison operators, string tests, file tests, and logical operators.

### 5. [Case/Switch Statements](05-case-switch.md)
Use case statements for clean, readable code when testing multiple conditions and pattern matching.

### 6. [For Loops](06-for-loops.md)
Loop through numbers, arrays, lists, and files using different for loop syntax variations.

### 7. [While Loops](07-while-loops.md)
Implement while and until loops for iterative operations based on dynamic conditions.

### 8. [Functions](08-functions.md)
Create reusable functions with parameters, return values, and proper error handling.

### 9. [String Manipulation](09-string-manipulation.md)
Extract substrings, replace text, convert case, trim whitespace, and validate patterns.

### 10. [Global and Local Variables](10-global-local-variables.md)
Understand variable scope, create local variables in functions, and manage configuration variables.

---

## 🎯 Learning Path

**Beginner:**
1. Variables & Basic Operations
2. Echo Behavior & Special Characters
3. User Input & Password Handling

**Intermediate:**
4. Conditional Statements
5. Case/Switch Statements
6. For Loops
7. While Loops

**Advanced:**
8. Functions
9. String Manipulation
10. Global and Local Variables

---

## 💡 Quick Reference

### Variable Declaration
```bash
name="Jayesh"
age=24
```

### Conditionals
```bash
if [ condition ]; then
    commands
elif [ condition2 ]; then
    commands
else
    commands
fi
```

### Loops
```bash
for i in {1..5}; do
    echo $i
done

while [ condition ]; do
    commands
done
```

### Functions
```bash
my_function() {
    local param=$1
    echo $param
}

my_function "argument"
```

---

## ✅ Best Practices

✅ Always quote variables: `"$var"`  
✅ Use meaningful names  
✅ Add comments to explain logic  
✅ Use `local` for function variables  
✅ Test edge cases  
✅ Handle errors gracefully  
✅ Keep scripts modular  

---

## 🔗 Navigation

- [Back to main README](../README.md)
- [View all examples](../examples/)
