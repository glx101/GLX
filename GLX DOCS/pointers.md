# GLX Pointer Documentation

---

## 1. Example
```glx
name = "danishk"

_ptr_ ptr1 = _addr_ name
```

Here:
* `name` is a normal variable
* `ptr1` stores the address of `name`

---

## 2. Pointer to Pointer (Chaining)

Pointers can point to other pointers.

### Example
```glx
_ptr_ ptr2 = _addr_ ptr1
_ptr_ ptr3 = _addr_ ptr2
```

This creates a chain:
```
ptr3 → ptr2 → ptr1 → name
```

---

## 3. Dereferencing a Pointer (Reading Value)

GLX uses brackets `[]` for dereferencing.

### Rule
* Number of brackets = dereference level

### Syntax and Meaning

| Syntax | Meaning |
|--------|---------|
| `[ptr]` | Dereference once |
| `[[ptr]]` | Dereference twice |
| `[[[ptr]]]` | Dereference three times |

### Example
```glx
print(src=[ptr1])        # value of name
print(src=[[ptr2]])      # value of name
print(src=[[[ptr3]]])    # value of name
```

---

## 4. Dereferencing using `_deref_`

You can also use the builtin `_deref_` explicitly.

### Example
```glx
print(src=_deref_[[[ptr3]]])
```

This reads the final value after all pointer levels.

---

## 5. Dereference Assignment (Writing Through Pointer)

Pointers can be used to modify values through dereferencing.

### Syntax
```glx
[[ptr]] = value
```

### Example
```glx
[[[ptr3]]] = "Alice"
print(src=name)
```

### Output
```
Alice
```

This modifies `name` through pointer chaining.

---

## 6. Pointer Assignment inside Labels (Functions)

Pointers work across labels and scopes.

### Example
```glx
label visit[] show(ptr=ptr3) {
    [[[ptr]]] = "Anoop Sinha"
    return nil
}

show(ptr=ptr3)
print(src=name)
```

### Output
```
Anoop Sinha
```

---

## 7. Full Working Example
```glx
name = "danishk"

_ptr_ ptr1 = _addr_ name
_ptr_ ptr2 = _addr_ ptr1
_ptr_ ptr3 = _addr_ ptr2

print(src=[[[ptr3]]])

_ptr_ ptr4 = _addr_ ptr3
print(src=[[[[ptr4]]]])

[[[[ptr4]]]] = "Alice"
print(src=[[[[ptr4]]]])

label visit[] show(ptr=ptr4) {
    [[[[ptr]]]] = "Anoop Sinha"
    return nil
}

show(ptr=ptr4)
print(src=[[[[ptr4]]]])
```

### Output
```
danishk
danishk
Alice
Anoop Sinha
```

---

## 8. Important Rules

* Pointers must be created using `_addr_`
* Dereference level must match pointer depth
* Assigning through a pointer modifies the original variable
* Dereferencing a non-pointer throws a runtime error

---

## 9. Why GLX Pointers are Powerful

GLX pointers provide:
* Reference semantics (like C/C++)
* Safe chained dereferencing
* Mutable shared state
* Function-level data manipulation
* Advanced scripting capabilities beyond Bash

GLX pointers make the language modern, expressive, and powerful.

## 10. Important Note on Scope and Pointer Safety
> When using pointers in GLX, always keep in mind the relationship between pointers and scope:
>Scope Awareness: Pointers only remain valid as long as their target variables or bindings are within the same scope or parent scope. If the variable goes out of scope, the pointer becomes invalid.
>Parent and Current Scope Usage: Use pointers when you are sure that the target variable will stay alive in the current or parent scope. This ensures that the pointer can safely access the variable.
>Avoid Cross-Scope Pointers: Do not use pointers that refer to variables in a scope that might end before the pointer is done being used. This will lead to invalid pointer errors.
>By following these precautions, you ensure that your pointers remain safe and that you avoid runtime errors related to scope. This makes your GLX programs more robust and reliable.

## 11. Array / Axis Pointer Arithmetic (NEW FEATURE)

```
GLX pointers can also point to Arrays or Axes (lists/tuples) and support C-style pointer arithmetic.

Key Behavior

_addr_ arr returns the address of the first element (arr[0])

Adding an integer to a pointer moves it to the next element

Dereferencing reads or writes the element at the current pointer position

Example
arr = [&l, 10, 20, 30, 40]

_ptr_ p = _addr_ arr  

print(src=_deref_[p])    # 10

p = p + 1
_deref_[p] = 99
print(src=_deref_[p])    # 99

p = p + 1
print(src=_deref_[p])    # 30

Explanation
p → arr[0] → 10
p + 1 → arr[1] → 20 → overwritten to 99
p + 2 → arr[2] → 30
```

>>> This allows sequential traversal and modification of array elements using pointers.