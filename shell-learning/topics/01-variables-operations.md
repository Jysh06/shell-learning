# 1. Variables & Basic Operations

## Overview
Variables are containers for storing data values. They allow you to store and manipulate information throughout your script.

## Declaring Variables

In shell scripting, variables are created by assigning a value to a name. No spaces are allowed around the equals sign.

```bash
variable_name=value
```

### Examples

```bash
name="Jayesh"
age="24"
city="New Delhi"
```

## Using Variables

To access the value of a variable, prefix it with a dollar sign `$`.

```bash
echo "Hello $name"
echo "Your age is $age"
```

---

## String Concatenation

Combine multiple strings by placing them adjacent to each other.

```bash
greetings="Hello"
name="Jayesh"
message="$greetings, $name"
echo "$message"
# Output: Hello, Jayesh
```

---

## String Length

Use `${#variable}` to get the length of a string.

```bash
string="Vishal Patil"
length=${#string}
echo "Length : $length"
# Output: Length : 12
```

---

## Arithmetic Operations

Perform calculations using `$(( ))` syntax.

```bash
x=4
y=7
sum=$((x + y))
echo "Sum: $sum"
# Output: Sum: 11
```

### Arithmetic Operators

| Operator | Description |
|----------|-------------|
| `+` | Addition |
| `-` | Subtraction |
| `*` | Multiplication |
| `/` | Division |
| `%` | Modulo (remainder) |

### Examples

```bash
a=10
b=3

sum=$((a + b))          # 13
diff=$((a - b))         # 7
prod=$((a * b))         # 30
div=$((a / b))          # 3
mod=$((a % b))          # 1

echo "Sum: $sum, Difference: $diff"
```

---

## Variable Scope

Variables are global by default and accessible throughout the script.

```bash
my_var="Global"
echo "$my_var"          # Output: Global
```

---

## Best Practices

✅ Use meaningful variable names  
✅ Quote variables to prevent word splitting: `"$var"`  
✅ Use `${var}` for clarity: `"${var}"`  
✅ Initialize variables before use  
✅ Avoid using reserved words as variable names

---

## Next Topic

→ [Echo Behavior & Special Characters](02-echo-special-characters.md)
