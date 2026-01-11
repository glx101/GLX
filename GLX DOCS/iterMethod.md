// ITER and ITER Assignment Documentation

//// Overview

`ITER` is a special syntax for accessing and modifying elements in data structures (dictionaries, arrays, and axis) in GLX. It provides a uniform interface for both reading and writing values.

//// Syntax

### Read Access
```glx
ITER["variable_name">>type, key_or_index]
```

### Write Access (Assignment)
```glx
ITER["variable_name">>type, key_or_index] = value
```

//// Parameters

- **variable_name**: A string literal representing the variable name
- **type**: The data structure type, one of:
  - `dict` - Dictionary/HashMap
  - `array` - Array/List
  - `axis` - Immutable axis/vector
- **key_or_index**: 
  - For `dict`: Any value convertible to string (string, int, float, byte, bool)
  - For `array`: Integer index
  - For `axis`: Integer index

---

//// Dictionary Access (`dict`)

### Reading from Dictionary

**Syntax:**
```glx
ITER["variable_name">>dict, key]
```

**Key Conversion:**
Dictionary keys are always stored and accessed as strings. Any key type is automatically converted to string:
- `String` → used as-is
- `Int` → converted via `to_string()`
- `Float` → converted via `to_string()`
- `Byte` → converted via `to_string()`
- `Bool` → converted via `to_string()`

**Return Value:**
- Returns the value associated with the key if it exists
- Returns `Nil` if the key doesn't exist

**Examples:**
```glx
data = [&d, "name":"Alice", "age":25, "active":true]

// String key
print(src=ITER["data">>dict, "name"])        // Output: Alice

// Integer key (converted to "25")
print(src=ITER["data">>dict, 25])            // Output: Nil (unless "25" exists as key)

// Accessing with variable
key = "age"
print(src=ITER["data">>dict, key])           // Output: 25
```

### Writing to Dictionary

**Syntax:**
```glx
ITER["variable_name">>dict, key] = value
```

**Behavior:**
- If key exists: Updates the value
- If key doesn't exist: Inserts new key-value pair
- Key is always converted to string

**Examples:**
```glx
data = [&d, "name":"Alice", "age":25]

// Update existing key
ITER["data">>dict, "name"] = "Bob"

// Add new key
ITER["data">>dict, "email"] = "bob@example.com"

// Using different key types (all converted to strings)
ITER["data">>dict, 100] = "hundred"          // Key becomes "100"
ITER["data">>dict, 3.14] = "pi"              // Key becomes "3.14"
ITER["data">>dict, true] = "yes"             // Key becomes "true"

print(src=data)
// Output: {"name":"Bob", "age":25, "email":"bob@example.com", "100":"hundred", "3.14":"pi", "true":"yes"}
```

---

//// Array Access (`array`)

### Reading from Array

**Syntax:**
```glx
ITER["variable_name">>array, index]
```

**Index Requirements:**
- Must be an integer (`Value::Int`)
- 0-based indexing
- Negative indices are not supported

**Return Value:**
- Returns the element at the specified index
- Returns error if index is out of bounds

**Examples:**
```glx
numbers = [&l, 10, 20, 30, 40, 50]

// Access first element
print(src=ITER["numbers">>array, 0])         // Output: 10

// Access middle element
print(src=ITER["numbers">>array, 2])         // Output: 30

// Access last element (manually calculate)
print(src=ITER["numbers">>array, 4])         // Output: 50

// Out of bounds - ERROR
print(src=ITER["numbers">>array, 10])        // Error: Array index 10 out of bounds (len=5)
```

### Writing to Array

**Syntax:**
```glx
ITER["variable_name">>array, index] = value
```

**Behavior:**
- Updates the element at the specified index
- Index must be within bounds (0 to length-1)
- Does NOT extend the array if index is out of bounds

**Examples:**
```glx
numbers = [&l, 10, 20, 30, 40, 50]

// Update first element
ITER["numbers">>array, 0] = 100

// Update middle element
ITER["numbers">>array, 2] = 300

print(src=numbers)                            // Output: [100, 20, 300, 40, 50]

// Out of bounds assignment - ERROR
ITER["numbers">>array, 10] = 999             // Error: Array index 10 out of bounds (len=5)
```

---

### Axis Access (`axis`)

### Reading from Axis

**Syntax:**
```glx
ITER["variable_name">>axis, index]
```

**Index Requirements:**
- Must be an integer (`Value::Int`)
- 0-based indexing

**Return Value:**
- Returns the element at the specified index
- Returns error if index is out of bounds

**Examples:**
```glx
coordinates = [&a, 10, 20, 30]

// Access elements
print(src=ITER["coordinates">>axis, 0])     // Output: 10
print(src=ITER["coordinates">>axis, 1])      //Output: 20
print(src=ITER["coordinates">>axis, 2])      //Output: 30

// Out of bounds - ERROR
print(src=ITER["coordinates">>axis, 5])      // Error: Axis index 5 out of bounds (len=3)
```

### Writing to Axis (NOT ALLOWED)

**Behavior:**
Axis is an **immutable** data structure (const vector). Any attempt to assign to an axis element will result in an error.

**Example:**
```glx
coordinates = [&a, 10, 20, 30]

// Attempted assignment - ERROR
ITER["coordinates">>axis, 0] = 100           // Error: Cannot assign to axis - axis is immutable (const vector)
```

---

### Error Handling

### Common Errors

###// 1. Variable Name Not a String
```glx
x = 123
ITER[x>>dict, "key"]                         // Error: Expected variable name as string
```

**Solution:** Use string literals for variable names
```glx
ITER["x">>dict, "key"]                       // Correct
```

###// 2. Type Mismatch
```glx
data = [&d, "name":"Alice"]
ITER["data">>array, 0]                       // Error: Expected array for ITER, got Dictionary
```

**Solution:** Use correct type specifier
```glx
ITER["data">>dict, "name"]                   // Correct
```

### 3. Invalid Index Type for Arrays
```glx
numbers = [&l, 10, 20, 30]
ITER["numbers">>array, "hello"]              // Error: Array index must be int, got String
```

**Solution:** Use integer indices
```glx
ITER["numbers">>array, 0]                    // Correct
```

### 4. Out of Bounds Access
```glx
numbers = [&l, 10, 20, 30]
ITER["numbers">>array, 100]                  // Error: Array index 100 out of bounds (len=3)
```

**Solution:** Ensure index is within valid range (0 to length-1)

//// 5. Unknown Type Specifier
```glx
ITER["data">>list, 0]                        // Error: Unknown iterable type 'list' (expected dict/array/axis)
```

**Solution:** Use valid type: `dict`, `array`, or `axis`

---

//// Complete Examples

// Example 1: User Profile Management
```glx
// Create user profile
profile = [&d, "username":"alice", "email":"alice@example.com", "age":25]

// Read values
print(src=ITER["profile">>dict, "username"])  // Output: alice
print(src=ITER["profile">>dict, "age"])       // Output: 25

// Update values
ITER["profile">>dict, "age"] = 26
ITER["profile">>dict, "email"] = "alice.new@example.com"

// Add new fields
ITER["profile">>dict, "country"] = "USA"
ITER["profile">>dict, "verified"] = true

print(src=profile)
// Output: {"username":"alice", "email":"alice.new@example.com", "age":26, "country":"USA", "verified":true}
```

// Example 2: Shopping Cart
```glx
// Create shopping cart
cart = [&l, "Apple", "Banana", "Orange"]

// Display items
print(src=ITER["cart">>array, 0])             // Output: Apple
print(src=ITER["cart">>array, 1])             // Output: Banana
print(src=ITER["cart">>array, 2])             // Output: Orange

// Update items
ITER["cart">>array, 0] = "Mango"
ITER["cart">>array, 2] = "Grapes"

print(src=cart)                                // Output: [Mango, Banana, Grapes]
```

### Example 3: Immutable Coordinates
```glx
// Create coordinate axis
point = [&a, 10, 20, 30]

// Read coordinates
x = ITER["point">>axis, 0]                    // x = 10
y = ITER["point">>axis, 1]                    // y = 20
z = ITER["point">>axis, 2]                    // z = 30

print(src=x)                                   // Output: 10
print(src=y)                                   // Output: 20
print(src=z)                                   // Output: 30

// Cannot modify axis
// ITER["point">>axis, 0] = 100               // Error: Cannot assign to axis
```

### Example 4: Nested Data Structures
```glx
// Create nested structure
user = [&d, 
    "name":"John", 
    "contacts":[&d, "email":"john@example.com", "phone":"123-456-7890"],
    "scores":[&l, 85, 90, 95]
]

// Access nested dictionary
contacts = ITER["user">>dict, "contacts"]
print(src=ITER["contacts">>dict, "email"])    // Note: Need to store intermediate result

// Access nested array
scores = ITER["user">>dict, "scores"]
print(src=ITER["scores">>array, 0])           // Note: Need to store intermediate result
```

---

//// Best Practices

### 1. Use Descriptive Variable Names
```glx
// Good
ITER["user_profile">>dict, "email"]

// Bad
ITER["x">>dict, "email"]
```

### 2. Validate Before Access
```glx
data = [&d, "name":"Alice"]

// Check if key might exist
value = ITER["data">>dict, "age"]
if value == Nil {
    print(src="Age not found")
}
```

### 3. Use Appropriate Data Structures
- **Dictionary**: Key-value pairs, named access
- **Array**: Ordered collections, mutable, indexed access
- **Axis**: Immutable vectors, read-only indexed access

### 4. Handle Errors Gracefully
```glx
// Instead of direct access that might fail
// index = 100
// ITER["numbers">>array, index]

// Validate first
numbers = [&l, 10, 20, 30]
// Add bounds checking logic before accessing
```

---

//// Performance Notes

1. **Dictionary Access**: O(1) average case for lookups and insertions
2. **Array Access**: O(1) for index-based access
3. **Axis Access**: O(1) for index-based access
4. **Key Conversion**: Minimal overhead for converting keys to strings

---

//// Limitations

1. **No chaining**: Currently, you cannot chain ITER operations directly
```glx
   // Not supported (yet)
   // ITER["user">>dict, "contacts"]ITER["dict", "email"]
   
   // Workaround: Use intermediate variables
   contacts = ITER["user">>dict, "contacts"]
   email = ITER["contacts">>dict, "email"]
```

2. **No negative indexing**: Arrays and axes don't support negative indices
```glx
   // Not supported
   // ITER["array">>array, -1]  // Cannot access last element this way
```

3. **No array extension**: Assignment to out-of-bounds index doesn't extend the array
```glx
   arr = [&l, 1, 2, 3]
   // ITER["arr">>array, 5] = 10  // Error, doesn't auto-extend
```

---

//// Summary

| Feature | Dictionary | Array | Axis |
|---------|-----------|-------|------|
| **Read Access** | ✅ Yes | ✅ Yes | ✅ Yes |
| **Write Access** | ✅ Yes | ✅ Yes | ❌ No (Immutable) |
| **Key/Index Type** | Any (→ String) | Integer only | Integer only |
| **Missing Key Behavior** | Returns `Nil` | Error | Error |
| **Out of Bounds** | N/A | Error | Error |
| **Auto-insert** | ✅ Yes | ❌ No | N/A |