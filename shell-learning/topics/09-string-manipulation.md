# 9. String Manipulation

## Overview
String manipulation is a powerful feature in shell scripting. It allows you to extract, replace, and transform strings without external programs.

---

## Substring Extraction

Extract a portion of a string using the syntax `${string:offset:length}`.

```bash
string="Hello,world"
substring=${string:6:5}
echo "$substring"
# Output: world
```

### More Examples

```bash
text="DevOps Engineer"

# Extract "DevOps" (start at 0, length 6)
echo "${text:0:6}"        # Output: DevOps

# Extract "Engineer" (start at 7, length 8)
echo "${text:7:8}"        # Output: Engineer

# From position 3 to end
echo "${text:3}"          # Output: Ops Engineer
```

---

## String Length

Get the length of a string using `${#string}`.

```bash
string="Vishal Patil"
length=${#string}
echo "Length: $length"
# Output: Length: 12
```

---

## String Replacement

### Replace First Occurrence

```bash
string1="ms dhoni, def"
search="def"
replace="faf du plessis"
result=${string1/$search/$replace}

echo "Original: $string1"
echo "Modified: $result"
```

**Output:**
```
Original: ms dhoni, def
Modified: ms dhoni, faf du plessis
```

### Replace All Occurrences

```bash
text="foo bar foo baz foo"
result=${text//foo/hello}

echo "Original: $text"
echo "Modified: $result"
# Output: Modified: hello bar hello baz hello
```

---

## Remove Substring

### Remove Pattern from End

```bash
filename="document.txt.bak"
name=${filename%.bak}
echo "$name"
# Output: document.txt
```

### Remove Pattern from Start

```bash
path="/home/user/documents"
relative=${path#/home/user/}
echo "$relative"
# Output: documents
```

### Remove All Occurrences

```bash
text="foo-bar-foo-baz"
result=${text//-/}
echo "$result"
# Output: foobarfoobaz
```

---

## Case Conversion (Bash 4+)

### Convert to Uppercase

```bash
text="hello world"
uppercase="${text^^}"
echo "$uppercase"
# Output: HELLO WORLD
```

### Convert to Lowercase

```bash
text="Hello World"
lowercase="${text,,}"
echo "$lowercase"
# Output: hello world
```

### Capitalize First Character

```bash
text="hello"
capitalized="${text^}"
echo "$capitalized"
# Output: Hello
```

---

## String Trimming

### Remove Leading/Trailing Whitespace

```bash
#!/bin/bash

trim() {
    local str="$1"
    str="${str#"${str%%[![:space:]]*}"}"   # Remove leading
    str="${str%"${str##*[![:space:]]}"}"   # Remove trailing
    echo "$str"
}

text="  hello world  "
echo "'$(trim "$text")'"
# Output: 'hello world'
```

---

## String Comparison

### Equality

```bash
str1="hello"
str2="hello"

if [ "$str1" = "$str2" ]; then
    echo "Strings are equal"
else
    echo "Strings are different"
fi
```

### Inequality

```bash
if [ "$str1" != "$str2" ]; then
    echo "Strings are different"
fi
```

---

## Check String Patterns

### Check if Contains Substring

```bash
text="Hello World"

if [[ $text == *"World"* ]]; then
    echo "Contains 'World'"
fi
```

### Check if Starts With

```bash
if [[ $text == "Hello"* ]]; then
    echo "Starts with 'Hello'"
fi
```

### Check if Ends With

```bash
if [[ $text == *"World" ]]; then
    echo "Ends with 'World'"
fi
```

---

## Regular Expression Matching

### Basic Pattern Matching

```bash
text="hello123world"

if [[ $text =~ [0-9]+ ]]; then
    echo "Contains numbers"
fi
```

### Extract Matched Groups

```bash
text="Name: John Age: 25"

if [[ $text =~ Name:\ ([A-Za-z]+)\ Age:\ ([0-9]+) ]]; then
    echo "Name: ${BASH_REMATCH[1]}"
    echo "Age: ${BASH_REMATCH[2]}"
fi
```

**Output:**
```
Name: John
Age: 25
```

---

## String Splitting

### Split String by Delimiter

```bash
IFS=',' read -ra words <<< "apple,banana,cherry"

for word in "${words[@]}"; do
    echo "$word"
done
```

**Output:**
```
apple
banana
cherry
```

---

## Practical Examples

### Validate Email Format

```bash
is_valid_email() {
    local email=$1
    
    if [[ $email =~ ^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$ ]]; then
        return 0
    else
        return 1
    fi
}

if is_valid_email "user@example.com"; then
    echo "Valid email"
fi
```

### Extract File Extension

```bash
get_extension() {
    local filename=$1
    echo "${filename##*.}"
}

filename="document.pdf"
ext=$(get_extension "$filename")
echo "Extension: $ext"
# Output: Extension: pdf
```

### Replace Variables in Template

```bash
#!/bin/bash

template="Hello \${name}, you have \${count} messages"
name="John"
count=5

result="${template//\\\${name}/$name}"
result="${result//\\\${count}/$count}"

echo "$result"
# Output: Hello John, you have 5 messages
```

---

## Complete String Manipulation Example

```bash
#!/bin/bash

# Extract, replace, and transform strings
file="my-project_2024-12-11.tar.gz"

# Remove compression extension
without_gz="${file%.gz}"
echo "Without gz: $without_gz"

# Remove tar extension
without_tar="${without_gz%.tar}"
echo "Without tar: $without_tar"

# Replace dashes with spaces
spaced="${without_tar//-/ }"
echo "Spaced: $spaced"

# Get length
echo "Length: ${#file}"

# Check if contains specific text
if [[ $file == *"project"* ]]; then
    echo "Filename contains 'project'"
fi
```

---

## Best Practices

✅ Quote variables: `"${var}"`  
✅ Use `${var}` syntax for clarity  
✅ Test regex patterns thoroughly  
✅ Use `[[ ]]` for string comparisons  
✅ Be careful with special characters  
✅ Use `IFS` when splitting strings  
✅ Document complex string operations  

---

## Next Topic

→ [Global and Local Variables](10-global-local-variables.md)
