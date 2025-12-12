# 15. Regular Expressions

## Overview
Regular expressions (regex) are patterns for matching text. In shell scripting, they're commonly used with `grep`, `sed`, and `awk` for pattern matching and text manipulation.

---

## Grep - Pattern Matching

Search for patterns in files:

```bash
grep "pattern" file.txt  # Find lines containing "pattern"
grep -E "^[0-9]+" file.txt  # Extended regex: lines starting with digits
```

---

## Sed - Stream Editor

Edit text streams:

```bash
sed 's/old/new/g' file.txt  # Replace all "old" with "new"
sed -E 's/([0-9]{3})/(\1)/g' file.txt  # Add parentheses around 3-digit numbers
```

---

## Awk - Text Processing

Process and analyze text:

```bash
awk '{print $1}' file.txt  # Print first column
awk '/pattern/ {print $2}' file.txt  # Print second column of lines matching "pattern"
awk '{sum += $1} END {print sum}' file.txt  # Sum first column
```

---

## Common Regex Patterns

- `^` : Start of line
- `$` : End of line
- `.` : Any single character
- `*` : Zero or more of previous
- `+` : One or more of previous
- `[abc]` : Any of a, b, or c
- `[0-9]` : Any digit

---

## Best Practices

✅ Test regex patterns thoroughly  
✅ Use extended regex (-E) for complex patterns  
✅ Quote patterns containing special characters  
✅ Use grep for searching, sed for editing, awk for processing  

---

## Next Topic

→ [Advanced Topics](16-advanced-topics.md)
