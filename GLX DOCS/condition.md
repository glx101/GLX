# Conditional Statements in glx Language

The glx Language provides `if`, `elif`, and `else` for decision-making. These blocks control execution flow based on boolean expressions.

## Basic Syntax
```
if condition {
    // code executes if condition is true
} elif another_condition {
    // executes if previous condition was false
} else {
    // executes if all conditions are false
}
```

## Rules

* Conditions can optionally be inside parentheses `()`
* Code blocks must be inside curly braces `{}`
* Only one block executes
* `elif` and `else` are optional
* Conditions are evaluated top to bottom

## Example 1: Numeric Comparison
```
x = 20

if x > 10 {
    print(src="x is greater than 10")
} elif x < 0 {
    print(src="x is a negative number")
} else {
    print(src="x is under 10")
}
```

### Execution Flow

1. `x > 10` → true
2. First `if` block executes
3. Remaining `elif` and `else` blocks are skipped

### Output
```
x is greater than 10
```

## How `elif` Works

* `elif` means "else if"
* It runs only if all previous conditions are false
* You can use multiple `elif` blocks
```
if a == 1 {
    ...
} elif a == 2 {
    ...
} elif a == 3 {
    ...
}
```

## How `else` Works

* `else` runs only when all conditions fail
* It has no condition
* It must be the last block

## Boolean Logic Support

glx Language supports:

* Logical OR: `||`
* Logical AND: `&&`
* Logical NOT: `!`
* Grouping using parentheses

## Example 2: Logical Expressions
```
if !(false || false) {
    print(src="!(false || false)")
}
```

### Step-by-Step Evaluation

1. `false || false` → `false`
2. `!(false)` → `true`
3. Condition passes → block executes

### Output
```
!(false || false)
```

## Parentheses Usage

Parentheses are optional for simple conditions but can be used for clarity or grouping:
```
// Both are valid
if x > 10 {
    ...
}

if (x > 10) {
    ...
}

// Parentheses useful for complex expressions
if (x > 10 && y < 20) || z == 0 {
    ...
}
```

## Key Notes

* Conditions must evaluate to true or false
* Boolean expressions can be nested
* Parentheses control evaluation order in complex expressions
* Parentheses are optional but can improve readability
* `if` blocks do not fall through

## Conceptual Summary

| Feature | Behavior |
|---------|----------|
| `if` | First condition check |
| `elif` | Secondary condition (optional, repeatable) |
| `else` | Default execution path |
| `!` | Negates a boolean |
| `&&` | Logical AND |
| `||` | Logical OR |
| `()` | Optional grouping for clarity |