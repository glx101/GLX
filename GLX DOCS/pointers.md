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

# `_ptr_add_` Function Documentation

## Purpose

The `_ptr_add_` function is designed to perform pointer arithmetic in the GLX language. It takes a pointer that references an element (typically within an array or axis) and increments that pointer by a specified number of elements. In other words, it moves the pointer forward by a given step size.

## How It Works

- `_ptr_add_` follows the pointer chain until it reaches the final pointer that directly references an element in the array or axis.

- Once it finds this final pointer, it increments the pointer's target address by the specified number of elements (the `step` parameter).

- This allows the pointer to move from one element to the next, just like pointer arithmetic in C or C++.

## Usage Example

In GLX, after defining a pointer to the start of an array, you can use `_ptr_add_` to move it to the next element. This lets you iterate through an array by incrementing the pointer step-by-step and dereferencing it to access each element.

## Important Consideration

Make sure to use `_ptr_add_` only with pointers that reference arrays or axes. Using it with pointers to single variables that are not part of a sequence can lead to invalid pointer references. This function essentially makes pointer arithmetic in GLX more convenient and safe when dealing with collections.

# Note on Pointer Arithmetic and `_ptr_add_`

In many cases, you might find that using the direct plus (`+`) operator for pointer arithmetic doesn't work as expected in GLX. This is because GLX does not always support normal arithmetic operators on pointers, especially when those pointers are referencing single variables (like integers or strings) rather than arrays or sequential memory blocks.

## Where the Plus Operator Won't Work

- **Single Variables:** If your pointer points to a single variable (like an integer or a string), applying the `+` operator directly to it may cause an error. GLX does not universally support arithmetic on all pointers.

- **Non-Sequential Memory Objects:** Similarly, if a pointer references an object that is not stored in continuous memory, using the `+` operator to increment it might not work as intended and can lead to errors.

## When to Use `_ptr_add_`

- **Arrays or Axes:** When you want to move pointers between elements of an array or an axis, you should use the `_ptr_add_` function. This function ensures that the pointer moves correctly to the next element without creating invalid references.

In summary, use `_ptr_add_` whenever you need to safely navigate through arrays or axes. This approach helps you avoid errors that occur when using the `+` operator directly on pointers that are not meant for arithmetic operations.

