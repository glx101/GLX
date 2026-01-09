# GLX Reference Docs: Iterable Array Generation

This document explains how to generate iterable arrays in GLX using the range syntax.

## Syntax
```
ITERABLE[start..end]
```

## Description

The `ITERABLE` keyword generates an array containing sequential integer values from `start` to `end` (inclusive).

**Key Points:**
* Both `start` and `end` are **included** in the generated array
* The range uses double dots `..` as the separator
* Values are generated as integers
* The array includes all numbers from start to end

## Examples

### Basic Usage
```
arr = ITERABLE[1..100]
```

This generates an array containing integers from 1 to 100 (inclusive):
```
[1, 2, 3, 4, 5, ..., 98, 99, 100]
```

### Small Range
```
numbers = ITERABLE[1..5]
// Result: [1, 2, 3, 4, 5]
```

### Starting from Zero
```
indices = ITERABLE[0..10]
// Result: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

### Negative Numbers
```
range = ITERABLE[-5..5]
// Result: [-5, -4, -3, -2, -1, 0, 1, 2, 3, 4, 5]
```

### Large Range
```
big_array = ITERABLE[1..1000]
// Result: [1, 2, 3, ..., 998, 999, 1000]
```

## Use Cases

### Loop Iteration
```
for i in ITERABLE[1..10] {
    print(src="Number: " + i)
}
```

### Index Generation
```
positions = ITERABLE[0..99]
// Use as array indices
```

### Test Data
```
test_values = ITERABLE[1..50]
// Generate test data quickly
```

## Important Notes

* ✅ **Inclusive Range**: Both start and end values are included in the array
* ✅ The range `[1..5]` produces 5 elements: `[1, 2, 3, 4, 5]`
* ✅ The range `[1..100]` produces 100 elements (1 through 100)
* ⚠️ Large ranges may consume memory - use wisely for very large arrays

## Comparison with Other Languages

| Language | Syntax | Inclusive? |
|----------|--------|------------|
| GLX | `ITERABLE[1..100]` | ✅ Both ends |
| Python | `range(1, 101)` | ❌ End exclusive |
| Ruby | `(1..100).to_a` | ✅ Both ends |
| JavaScript | `Array.from({length: 100}, (_, i) => i + 1)` | Manual |

GLX's `ITERABLE` provides a simple, readable way to generate inclusive integer ranges.