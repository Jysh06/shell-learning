# 10. Global and Local Variables

## Overview
Understanding variable scope is crucial for writing maintainable shell scripts. Scope determines where a variable can be accessed.

---

## Global Variables

Global variables are accessible throughout the entire script and all functions.

```bash
#!/bin/bash

# Global variable
app_name="MyApp"
version="1.0"

print_info() {
    echo "App: $app_name, Version: $version"
}

print_info
# Output: App: MyApp, Version: 1.0
```

### Global Variables Remain Accessible

```bash
#!/bin/bash

global_var="I am global"

function_one() {
    echo "In function_one: $global_var"
}

function_two() {
    echo "In function_two: $global_var"
}

function_one
function_two

echo "In main: $global_var"
```

**Output:**
```
In function_one: I am global
In function_two: I am global
In main: I am global
```

---

## Local Variables

Local variables declared with the `local` keyword are only accessible within the function where they're declared.

```bash
#!/bin/bash

local_var="I am global"

my_function() {
    local local_var="I am local"
    echo "Inside function: $local_var"
}

my_function
echo "Outside function: $local_var"
```

**Output:**
```
Inside function: I am local
Outside function: I am global
```

### Local Variables in Functions

```bash
#!/bin/bash

calculate_sum() {
    local num1="$1"
    local num2="$2"
    local sum=$((num1 + num2))
    
    echo "$sum"
}

result=$(calculate_sum 10 20)
echo "Sum is $result"
echo "num1 = $num1"  # Empty (num1 is local to function)
```

**Output:**
```
Sum is 30
num1 =
```

---

## Global and Local Variables Example

```bash
#!/bin/bash

# Global variables
global_var="I'm a global variable"
config_file="/etc/config.conf"

local_variable() {
    # Local variables
    local local_var="Hello I am local"
    local temp_data="Temporary data"
    
    echo "Inside function:"
    echo "  Local: $local_var"
    echo "  Global: $global_var"
    echo "  Temp: $temp_data"
}

local_variable

echo ""
echo "Outside function:"
echo "  Global: $global_var"
echo "  Local: $local_var"       # Empty
echo "  Temp: $temp_data"        # Empty
echo "  Config: $config_file"
```

**Output:**
```
Inside function:
  Local: Hello I am local
  Global: I'm a global variable
  Temp: Temporary data

Outside function:
  Global: I'm a global variable
  Local: 
  Temp: 
  Config: /etc/config.conf
```

---

## Modifying Global Variables from Functions

Functions can modify global variables.

```bash
#!/bin/bash

counter=0

increment() {
    counter=$((counter + 1))
}

echo "Initial counter: $counter"

increment
echo "After increment: $counter"

increment
increment
echo "After 2 more increments: $counter"
```

**Output:**
```
Initial counter: 0
After increment: 1
After 2 more increments: 3
```

---

## Variable Shadowing

A local variable with the same name as a global variable hides (shadows) the global variable inside the function.

```bash
#!/bin/bash

name="Global Name"

display() {
    local name="Local Name"
    echo "Inside function: $name"
}

display
echo "Outside function: $name"
```

**Output:**
```
Inside function: Local Name
Outside function: Global Name
```

### Accessing Global Variable When Shadowed

```bash
#!/bin/bash

name="Global Name"

display() {
    local name="Local Name"
    echo "Local: $name"
    eval echo "Global: \$$GLOBAL_VAR"  # Access global (advanced)
}

GLOBAL_VAR=name  # Store variable name
display
```

---

## Best Practices for Variable Scope

### Use Local Variables in Functions

```bash
# ❌ BAD - Variables pollute global scope
sum_values() {
    num1=$1
    num2=$2
    result=$((num1 + num2))
    echo "$result"
}

# ✅ GOOD - Local variables
sum_values() {
    local num1=$1
    local num2=$2
    local result=$((num1 + num2))
    echo "$result"
}
```

### Clear Naming for Global Variables

```bash
# Use UPPERCASE for global constants
readonly SCRIPT_NAME="MyScript"
readonly VERSION="1.0"
readonly CONFIG_DIR="/etc/myapp"

# Use lowercase for global variables
log_file="/var/log/app.log"
debug_mode=0

# Use lowercase for local variables
function process_data() {
    local input_file=$1
    local output_file=$2
}
```

---

## Readonly Variables

Make variables immutable with `readonly`.

```bash
#!/bin/bash

readonly app_name="MyApplication"
readonly version="2.0"

echo "$app_name v$version"

app_name="NewName"  # Error: readonly variable
```

---

## Exporting Variables

Make variables available to child processes with `export`.

```bash
#!/bin/bash

export MY_VAR="Available to child processes"
local_var="Not exported"

bash -c 'echo "Child sees: $MY_VAR"'
bash -c 'echo "Child sees: $local_var"'
```

**Output:**
```
Child sees: Available to child processes
Child sees: 
```

---

## Complete Example: Configuration Management

```bash
#!/bin/bash

# Global configuration
readonly APP_NAME="DataProcessor"
readonly VERSION="1.0"
readonly LOG_FILE="/var/log/app.log"

config_loaded=0
debug_mode=0

load_config() {
    local config_file=$1
    
    if [ ! -f "$config_file" ]; then
        echo "Error: Config file not found"
        return 1
    fi
    
    source "$config_file"
    config_loaded=1
    
    return 0
}

process_file() {
    local input=$1
    local output=$2
    
    if [ ! -f "$input" ]; then
        echo "Error: Input file not found" >> "$LOG_FILE"
        return 1
    fi
    
    # Process the file
    cp "$input" "$output"
    
    echo "Processed: $input -> $output" >> "$LOG_FILE"
    return 0
}

# Main
if load_config "./config.conf"; then
    echo "Config loaded successfully"
    process_file "data.txt" "output.txt"
else
    echo "Failed to load config"
    exit 1
fi
```

---

## Best Practices Summary

✅ Use `local` for all function variables  
✅ Use UPPERCASE for readonly constants  
✅ Use lowercase for global variables  
✅ Document variable scope in comments  
✅ Avoid variable shadowing when possible  
✅ Make configuration variables `readonly`  
✅ Keep global variables minimal  
✅ Export only necessary variables  

---

## Next Topic

→ [Advanced Scripting Techniques](11-advanced-techniques.md)
