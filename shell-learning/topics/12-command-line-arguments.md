# 12. Command Line Arguments

## Overview
Bash scripts can accept arguments passed from the command line. These are accessible via special variables that provide information about the script execution and input parameters.

---

## Basic Argument Variables

```bash
#!/bin/bash
echo "Script name: $0"        # The name of the script itself
echo "First argument: $1"     # First argument passed to the script
echo "Second argument: $2"    # Second argument passed to the script
echo "Total number of arguments: $#"  # Total count of arguments (excluding script name)
echo "All arguments as list: $@"      # All arguments as separate words (preserves spaces)
echo "All arguments as string: $*"    # All arguments as a single string
```

**Example Usage:**
```bash
$ ./script.sh arg1 arg2 arg3
Script name: ./script.sh
First argument: arg1
Second argument: arg2
Total number of arguments: 3
All arguments as list: arg1 arg2 arg3
All arguments as string: arg1 arg2 arg3
```

---

## Usage in Scripts

Command line arguments are commonly used to make scripts flexible and reusable:

- Pass filenames to process
- Provide configuration options
- Specify input/output paths
- Control script behavior

---

## Best Practices

✅ Always validate arguments before using them  
✅ Provide usage information when arguments are missing or invalid  
✅ Use descriptive variable names when storing arguments  
✅ Quote arguments containing spaces: `"$1"`  

---

## Next Topic

→ [Error Handling](13-error-handling.md)
