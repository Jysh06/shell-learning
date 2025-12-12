# 11. Arrays

## Overview
Arrays in Bash allow storing multiple values in a single variable. They are zero-indexed and can be manipulated with various operations like adding, deleting, and iterating.

---

## Declaration and Access

```bash
fruits=("apple" "banana" "cherry" "orange")

echo "Fruits first ${fruits[0]}"  # Output: Fruits first apple
echo "Fruits fourth ${fruits[3]}" # Output: Fruits fourth orange
```

---

## For Loop in Arrays

Iterate through all elements using a for loop:

```bash
for fruit in "${fruits[@]}"; do
    echo "fruits in $fruit"
done
```

**Output:**
```
fruits in apple
fruits in banana
fruits in cherry
fruits in orange
```

---

## Deleting Elements (Unset)

Remove an element by index:

```bash
unset fruits[3]  # Removes "orange"
```

After unsetting, the array becomes: `("apple" "banana" "cherry")`

---

## Adding Elements (Append)

Add new elements to the end:

```bash
fruits+=(grapes)  # Adds "grapes"
echo "ADD --- ${fruits[@]}"  # Output: ADD --- apple banana cherry grapes
```

---

## Array Length

Get the number of elements:

```bash
length=${#fruits[@]}
echo "LENGTH ---->>> $length"  # Output: LENGTH ---->>> 4
```

---

## Best Practices

✅ Always quote array expansions: `"${array[@]}"`  
✅ Use descriptive array names  
✅ Be careful with spaces in array elements  

---

## Next Topic

→ [Command Line Arguments](12-command-line-arguments.md)
