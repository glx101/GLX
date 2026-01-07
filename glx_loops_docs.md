# GLX Loop Statements Documentation

## Overview

GLX provides three types of loop constructs for iterating and repeating code execution: `for` loops, `while` loops, and `do-while` loops. Each serves different use cases depending on when the loop condition needs to be evaluated.

## For Loop

The `for` loop iterates over a sequence of values, commonly used with ranges.

### Syntax

```glx
for variable _in_ sequence {
    // code block
}
```

### Components

- **variable**: The iterator variable that takes each value from the sequence
- **`_in_`**: Keyword connecting the variable to the sequence (note the underscores)
- **sequence**: A range or collection to iterate over
- **Range syntax**: `ITERABLE[start..end]` creates a range from start to end (inclusive)

### Examples

**Basic range iteration:**
```glx
for item _in_ ITERABLE[1..100] {
    kprint item
}
```
Output: Prints numbers from 1 to 100

**Different range examples:**
```glx
// Count from 0 to 9
for i _in_ ITERABLE[0..9] {
    kprint i
}

// Count from 5 to 15
for num _in_ ITERABLE[5..15] {
    kprint num
}

// Single iteration
for x _in_ ITERABLE[1..1] {
    kprint x
}

for item _in_ [&l, 33, 22, 44, 66, 1, 2, 3, 4] {
    print(src=item)
}

```

### Use Cases

- Iterating a known number of times
- Processing sequential numeric values
- Working with ranges of data
- Index-based operations

---

## While Loop

The `while` loop executes a code block repeatedly as long as a condition remains true. The condition is checked **before** each iteration.

### Syntax

```glx
while condition {
    // code block
}
```

### Components

- **condition**: Boolean expression evaluated before each iteration
- **code block**: Executes only if condition is true

### Examples

**Basic counter:**
```glx
count = 0
while count < 10 {
    kprint count
    count = count++
}

PATH=[/home/danishk/Downloads/GLX/GLX-main] USER=[danishk]% ./src/Test/binary.glx
0
1
2
3
4
5
6
7
8
9
PATH=[/home/danishk/Downloads/GLX/GLX-main] USER=[danishk]% 
```
Output: Prints numbers from 0 to 9

**Conditional processing:**
```glx
value = 100
while value > 0 {
    kprint value
    value = value - 10
}
```
Output: Prints 100, 90, 80, ..., 10

**Using comparison operators:**
```glx
x = 1
while x <= 5 {
    kprint x
    x = x + 1
}
```

### Use Cases

- Unknown number of iterations
- Condition-dependent loops
- Processing until a state changes
- Input validation loops

### Important Notes

- If the condition is false initially, the loop body never executes
- Always ensure the condition will eventually become false to avoid infinite loops
- The loop variable must be updated inside the loop body

---

## Do-While Loop

The `do-while` loop executes a code block at least once, then repeats as long as the condition remains true. The condition is checked **after** each iteration.

### Syntax

```glx
do {
    // code block
} while condition
```

### Components

- **code block**: Executes at least once before condition check
- **condition**: Boolean expression evaluated after each iteration

### Examples

**Basic usage:**
```glx
count = 0
do {
    kprint count
    count = count + 1
} while count < 20
```
Output: Prints numbers from 0 to 19

**Guaranteed execution:**
```glx
value = 100
do {
    kprint value
    value = value + 10
} while value < 50
```
Output: Prints 100 (executes once even though condition is false)

**Menu-style loop:**
```glx
choice = 0
do {
    kprint "Processing..."
    choice = choice + 1
} while choice < 3
```

### Use Cases

- Ensuring code executes at least once
- Menu systems
- Validation loops where initial attempt is required
- Post-condition loops

### Key Difference from While

**While Loop:**
```glx
x = 10
while x < 5 {
    kprint x  // Never executes
}
```

**Do-While Loop:**
```glx
x = 10
do {
    kprint x  // Executes once: prints 10
} while x < 5
```

---

## Loop Comparison

| Feature | For Loop | While Loop | Do-While Loop |
|---------|----------|------------|---------------|
| **Condition Check** | Implicit (range) | Before iteration | After iteration |
| **Minimum Executions** | 0 | 0 | 1 |
| **Best For** | Known iterations | Unknown iterations | At least one iteration |
| **Counter Management** | Automatic | Manual | Manual |

---

## Common Patterns

### Counting Up
```glx
// For loop
for i _in_ ITERABLE[1..10] {
    kprint i
}

// While loop
i = 1
while i <= 10 {
    kprint i
    i = i + 1
}
```

### Counting Down
```glx
// While loop
i = 10
while i > 0 {
    kprint i
    i = i - 1
}
```

### Nested Loops
```glx
for i _in_ ITERABLE[1..3] {
    for j _in_ ITERABLE[1..3] {
        kprint i
        kprint j
    }
}
```

### Accumulator Pattern
```glx
sum = 0
for num _in_ ITERABLE[1..100] {
    sum = sum + num
}
kprint sum  // Prints 5050
```

---

## Best Practices

1. **Choose the right loop type:**
   - Use `for` when you know the number of iterations
   - Use `while` when the number of iterations depends on a condition
   - Use `do-while` when you need guaranteed first execution

2. **Avoid infinite loops:**
   ```glx
   // BAD: Infinite loop
   count = 0
   while count < 10 {
       kprint count
       // Missing: count = count + 1
   }
   
   // GOOD: Proper termination
   count = 0
   while count < 10 {
       kprint count
       count = count + 1
   }
   ```

3. **Keep loop bodies simple:**
   - Extract complex logic into functions
   - Maintain clear loop variables
   - Use meaningful variable names

4. **Update loop variables correctly:**
   - Increment/decrement in the right direction
   - Ensure progress toward termination condition

5. **For loop ranges:**
   - Remember ranges are inclusive: `[1..10]` includes both 1 and 10
   - Use appropriate start and end values

---

## Notes

- **`kprint`**: GLX's print function for outputting values
- **Operators**: `+`, `-`, `<`, `>`, `<=`, `>=` work as expected
- **Range syntax**: `ITERABLE[start..end]` is specific to GLX for creating numeric ranges
- **`_in_` keyword**: Note the underscores - this is the exact syntax required
- **No break/continue**: Based on the examples, GLX may not support break/continue statements (documentation would need confirmation)

---

## Performance Considerations

- For loops with ranges are generally most efficient for known iterations
- While loops have minimal overhead but require manual counter management
- Do-while loops have the same performance as while loops but guarantee execution

---

## Common Errors

**Incorrect `_in_` syntax:**
```glx
// WRONG
for item in ITERABLE[1..10] { }

// CORRECT
for item _in_ ITERABLE[1..10] { }
```

**Off-by-one errors:**
```glx
// If you want 10 iterations starting from 0:
for i _in_ ITERABLE[0..9] { }  // Correct: 0,1,2,...,9

// Not:
for i _in_ ITERABLE[0..10] { }  // Wrong: gives 11 iterations
```

**Forgetting to update loop variable:**
```glx
// Infinite loop
count = 0
while count < 10 {
    kprint count
    // Forgot: count = count + 1
}
```

## Break and Continue, loop halt
```
break and continue to halt loop
```