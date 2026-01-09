# Switch–Case in GLX

In GLX, the switch–case statement is a structured control-flow construct used to execute one block of code from multiple possibilities based on the value of a single evaluated expression. It is designed to be clean, readable, and deterministic, making it a better alternative to long chains of if–elif–else statements when checking one variable against multiple fixed values.

## Expression Evaluation in Switch and Cases

Both the **switch target** and **case values** support full expression evaluation in GLX. This means you can use computed expressions, not just literals or variables.

### Switch Expression
The expression inside `switch ( ... )` is evaluated once. Its resulting value is used for comparison with each case. 

Example:
```glx
age = 2 + 3
switch (age) {
    // age evaluates to 5
}
```

### Case Expressions
Each `case` can also contain an expression that is evaluated before comparison. This allows for dynamic and computed match values.

Example:
```glx
y = 17
switch (y) {
    case (22+(-5)) {
        print(src="Working, Best")
    }
    case (20+2) {
        print(src="Nice, working")
    }
    case ("danishk"+" sinha") {
        print(src="Great")
    }
}
```

In this example:
- `y = 17` is evaluated
- `case (22+(-5))` evaluates to `17` and matches
- Output: `Working, Best`

## Key Components in GLX Switch–Case

### switch expression
The expression inside `switch ( ... )` is evaluated once. Its resulting value is used for comparison with each case. In GLX, this expression can be a computed value, not just a variable.

### case blocks
Each case defines a match value (which can be an expression) followed by a code block enclosed in braces `{ }`. When the switch value matches a case value exactly, only that case's block is executed.

**Important**: Case expressions are evaluated in order, and comparison happens after evaluation. This means:
- Arithmetic expressions: `case (10 + 5)` evaluates to `15`
- String concatenation: `case ("hello" + " world")` evaluates to `"hello world"`
- Complex expressions: Any valid GLX expression can be used

### implicit break behavior
Unlike C-like languages, GLX does not require an explicit `break` statement. Once a matching case is executed, control automatically exits the switch block. This eliminates accidental fall-through bugs and keeps logic predictable.

### default block
The `default` block is optional and is executed only when no case value matches the switch expression. It acts as a safe fallback, similar to `else` in conditional statements.

## Execution Flow in GLX

1. The expression inside `switch` is evaluated
2. Each `case` expression is evaluated in order
3. The switch value is compared against each evaluated case value
4. When a match is found, the corresponding case block is executed
5. The switch statement terminates immediately after executing the matched case
6. If no case matches and a `default` block exists, the default block is executed

## Examples

### Example 1: Computed Switch Expression
```glx
age = 2 + 3
switch (age) {
    case 2 {
        print(src="age is 2")
    }
    case 3 {
        print(src="age is 3")
    }
    case 5 {
        print(src="age is 5")
    }
    default {
        print(src="No such age")
    }
}
```

**Execution:**
- `age` evaluates to `5`
- `case 5` matches
- **Output:** `age is 5`

### Example 2: String Matching
```glx
os = "linux"
switch (os) {
    case "win" {
        print(src="Windows OS")
    }
    case "linux" {
        print(src="Linux Os")
    }
    case "darwin" {
        print(src="MacOS")
    }
}
```

**Output:** `Linux Os`

### Example 3: Computed Case Expressions
```glx
y = 17
switch (y) {
    case (22+(-5)) {
        print(src="Working, Best")
    }
    case (20+2) {
        print(src="Nice, working")
    }
    case ("danishk"+" sinha") {
        print(src="Great")
    }
}
```

**Execution:**
- `y = 17`
- `case (22+(-5))` evaluates to `17` → **Match found**
- **Output:** `Working, Best`

## Complete Test Output
```
PATH=[/home/danishk/Documents/GLX] USER=[danishk]% ./Test.glx
age is 5
Linux Os
PATH=[/home/danishk/Documents/GLX] USER=[danishk]%
```

## Summary

GLX switch–case behavior is:
- **Expression-driven**: Both switch targets and case values can be expressions
- **Type-flexible**: Supports integers, strings, and other comparable types
- **Safe**: No fall-through by design
- **Non-fallthrough**: Automatic exit after match
- **Predictable**: Deterministic execution flow

This makes GLX switch statements ideal for clear, maintainable, and bug-free control flow.