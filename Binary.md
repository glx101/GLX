# Operators in glx Language

The glx Language supports a comprehensive set of operators for arithmetic, comparison, logical operations, and more.

## Unary Operators

Unary operators work on a single operand.

| Operator | Name | Description | Supported Types | Example |
|----------|------|-------------|-----------------|---------|
| `-` | Negation | Negates a number | `Int`, `Float` | `-5`, `-3.14` |
| `!` | Logical NOT | Inverts boolean value | All types (uses truthiness) | `!true`, `!false` |
| `++` | Increment | Increases value by 1 | `Int`, `Float`, `UInt` | `x++`, `++x` |
| `--` | Decrement | Decreases value by 1 | `Int`, `Float`, `UInt` | `x--`, `--x` |

### Unary Examples
```
// Negation
x = 10
y = -x  // y = -10

z = -3.5  // z = -3.5

// Logical NOT
flag = true
result = !flag  // result = false

// Works with truthiness
value = 0
check = !value  // check = true (0 is falsy)
```

## Increment and Decrement Operators

The `++` and `--` operators modify variables in place.

### Prefix vs Postfix

| Type | Syntax | Returns | Description |
|------|--------|---------|-------------|
| Prefix | `++x` | New value | Increments first, then returns new value |
| Prefix | `--x` | New value | Decrements first, then returns new value |
| Postfix | `x++` | Old value | Returns old value, then increments |
| Postfix | `x--` | Old value | Returns old value, then decrements |

### Increment/Decrement Examples
```
// Prefix increment
x = 5
y = ++x  // x = 6, y = 6

// Postfix increment
x = 5
y = x++  // x = 6, y = 5

// Prefix decrement
x = 5
y = --x  // x = 4, y = 4

// Postfix decrement
x = 5
y = x--  // x = 5, y = 4

// Works with different number types
count = 10      // Int
count++         // count = 11

price = 99.99   // Float
price++         // price = 100.99

size = 5u       // UInt
size++          // size = 6u
```

### UInt Underflow Protection
```
x = 0  // Int with value 0

x = cast_type(value=x, type=__UINT__)

print(src=x)
print(src=typeof(src=x))

print(src=x--)
```

## Arithmetic Operators

Binary operators for mathematical operations.

| Operator | Name | Description | Example | Result |
|----------|------|-------------|---------|--------|
| `+` | Addition | Adds two numbers or concatenates strings | `5 + 3` | `8` |
| `-` | Subtraction | Subtracts right from left | `10 - 4` | `6` |
| `*` | Multiplication | Multiplies two numbers | `6 * 7` | `42` |
| `/` | Division | Divides left by right | `20 / 4` | `5` |
| `%` | Modulo | Returns remainder of division | `17 % 5` | `2` |

### Arithmetic Examples
```
// Addition
result = 10 + 5        // result = 15
sum = 3.5 + 2.5        // sum = 6.0

// String concatenation
greeting = "Hello" + " " + "World"  // "Hello World"

// Subtraction
diff = 20 - 8          // diff = 12

// Multiplication
product = 6 * 7        // product = 42

// Division
quotient = 100 / 4     // quotient = 25
decimal = 7 / 2        // decimal = 3.5 (if Float)

// Modulo
remainder = 17 % 5     // remainder = 2
even_check = 10 % 2    // even_check = 0
```

### Division by Zero Protection
```
x = 10 / 0   // ERROR: Division by zero

y = 15 % 0   // ERROR: Division by zero
```

## Comparison Operators

Operators that compare two values and return a boolean.

| Operator | Name | Description | Example | Result |
|----------|------|-------------|---------|--------|
| `==` | Equal | Checks if values are equal | `5 == 5` | `true` |
| `!=` | Not Equal | Checks if values are not equal | `5 != 3` | `true` |
| `>` | Greater Than | Checks if left is greater than right | `10 > 5` | `true` |
| `>=` | Greater or Equal | Checks if left is greater than or equal to right | `5 >= 5` | `true` |
| `<` | Less Than | Checks if left is less than right | `3 < 7` | `true` |
| `<=` | Less or Equal | Checks if left is less than or equal to right | `5 <= 5` | `true` |

### Comparison Examples
```
// Equality
x = 10
y = 10
result = x == y        // result = true

// Inequality
a = 5
b = 3
check = a != b         // check = true

// Greater than
if 100 > 50 {
    print(src="100 is greater")
}

// Greater than or equal
age = 18
can_vote = age >= 18   // can_vote = true

// Less than
temperature = 15
is_cold = temperature < 20  // is_cold = true

// Less than or equal
score = 75
passing = score <= 100      // passing = true
```

### Comparison Type Compatibility
```
// Comparing same types
5 == 5         // true
5.0 == 5.0     // true
"hi" == "hi"   // true

// Comparing different values
10 > 5         // true
3.5 < 7.2      // true

// Boolean comparisons
true == true   // true
false != true  // true
```

## Logical Operators

Operators for boolean logic with short-circuit evaluation.

| Operator | Name | Description | Short-circuit Behavior |
|----------|------|-------------|------------------------|
| `&&` | Logical AND | Returns true if both operands are truthy | If left is falsy, returns left without evaluating right |
| `||` | Logical OR | Returns true if either operand is truthy | If left is truthy, returns left without evaluating right |

### Logical Operator Truth Table

#### AND (`&&`)

| Left | Right | Result |
|------|-------|--------|
| `true` | `true` | `true` |
| `true` | `false` | `false` |
| `false` | `true` | `false` |
| `false` | `false` | `false` |

#### OR (`||`)

| Left | Right | Result |
|------|-------|--------|
| `true` | `true` | `true` |
| `true` | `false` | `true` |
| `false` | `true` | `true` |
| `false` | `false` | `false` |

### Logical Examples
```
// AND operator
result = true && true    // result = true
result = true && false   // result = false
result = false && true   // result = false

// OR operator
result = true || false   // result = true
result = false || false  // result = false

// Complex conditions
age = 25
has_license = true

can_drive = age >= 18 && has_license  // can_drive = true

// OR conditions
is_weekend = day == "Saturday" || day == "Sunday"

// Combining operators
if (age >= 18 && age <= 65) || is_student {
    print(src="Eligible for discount")
}
```

### Short-Circuit Evaluation
```
// AND short-circuit
// If left is false, right is never evaluated
false && expensive_function()  // expensive_function() NOT called

// OR short-circuit
// If left is true, right is never evaluated
true || expensive_function()   // expensive_function() NOT called

// Practical example
if user != null && user.is_active {
    // Safe: user.is_active only checked if user is not null
}
```

### Truthiness in Logical Operations

glx Language uses truthiness for logical operations:

| Value | Truthy? |
|-------|---------|
| `true` | Yes |
| `false` | No |
| `0` | No |
| Non-zero numbers | Yes |
| Empty string `""` | No |
| Non-empty strings | Yes |
| `null` | No |
```
// Using truthiness
x = 5
if x {  // x is truthy (non-zero)
    print(src="x is truthy")
}

y = 0
if !y {  // y is falsy (zero)
    print(src="y is falsy")
}
```

## Operator Precedence

Operators are evaluated in the following order (highest to lowest):

| Precedence | Operators | Description |
|------------|-----------|-------------|
| 1 (Highest) | `++`, `--` (postfix) | Postfix increment/decrement |
| 2 | `!`, `-`, `++`, `--` (prefix) | Unary operators |
| 3 | `*`, `/`, `%` | Multiplicative |
| 4 | `+`, `-` | Additive |
| 5 | `<`, `<=`, `>`, `>=` | Relational |
| 6 | `==`, `!=` | Equality |
| 7 | `&&` | Logical AND |
| 8 (Lowest) | `||` | Logical OR |

### Precedence Examples
```
// Multiplication before addition
result = 2 + 3 * 4      // result = 14 (not 20)

// Comparison before logical AND
check = 5 > 3 && 10 < 20  // check = true

// Using parentheses to override precedence
result = (2 + 3) * 4    // result = 20

// Complex expression
value = 10 + 5 * 2 - 3  // value = 17
// Evaluated as: 10 + (5 * 2) - 3 = 10 + 10 - 3 = 17
```

## Type Compatibility Matrix

### Arithmetic Operations (`+`, `-`, `*`, `/`, `%`)

| Left Type | Right Type | Result Type | Supported Operations |
|-----------|------------|-------------|----------------------|
| `Int` | `Int` | `Int` | All |
| `Float` | `Float` | `Float` | All |
| `Int` | `Float` | `Float` | All |
| `Float` | `Int` | `Float` | All |
| `UInt` | `UInt` | `UInt` | All |
| `String` | `String` | `String` | `+` only (concatenation) |

### Comparison Operations (`==`, `!=`, `>`, `>=`, `<`, `<=`)

All types support `==` and `!=`. Numeric types (`Int`, `Float`, `UInt`) support all comparison operators.

## Error Handling

### Common Operator Errors
```
// Type mismatch
x = "hello" - 5        // ERROR: Invalid operation

// Division by zero
y = 10 / 0             // ERROR: Division by zero

// Invalid unary operation
z = -"text"            // ERROR: Invalid unary operation

// Increment/decrement on non-variables
result = 5++           // ERROR: ++/-- target must be a variable

// Increment/decrement on non-numbers
text = "hello"
text++                 // ERROR: ++/-- works only on numbers

// UInt underflow
count = 0u
count--                // ERROR: uint underflow in --
```

## Summary

The glx Language provides:
- **4 unary operators** for negation, logical NOT, increment, and decrement
- **5 arithmetic operators** for basic math operations
- **6 comparison operators** for value comparisons
- **2 logical operators** with short-circuit evaluation
- **Type-safe operations** with clear error messages
- **Automatic type coercion** for compatible numeric types
- **Protection** against division by zero and unsigned underflow