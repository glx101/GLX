# GLX Switch Statement Documentation

## Overview

The `switch` statement in GLX provides a control flow mechanism for executing different code blocks based on the value of an expression. It offers a cleaner alternative to multiple `if-else` statements when comparing a single value against multiple cases.

## Syntax

```glx
switch(expression) {
    case value1 {
        // code block
    }
    case value2 {
        // code block
    }
    default {
        // code block executed when no case matches
    }
}
```

## Components

### Switch Expression
The expression in parentheses after `switch` is evaluated once, and its result is compared against each case value.

### Case Blocks
- Each `case` keyword is followed by a value or expression to match against
- Case values can be:
  - Literal numbers: `case 45`
  - Arithmetic expressions: `case 20-0`
  - String literals: `case "20"`
- Code blocks are enclosed in curly braces `{}`
- No explicit `break` statement is needed (no fall-through behavior)

### Default Block
- Optional `default` case executes when no other case matches
- Typically placed at the end of the switch statement

## Features

### Expression Evaluation in Cases
GLX allows expressions in case values, not just literals:

```glx
y = 20
switch (y) {
    case 20-0 {        // Evaluates to 20
        print(src="Match")
    }
    case 10+10 {       // Also evaluates to 20
        print(src="Another match")
    }
}

Switch Not Evaluate, but no error
```

### Type Sensitivity
Cases are type-sensitive. Numeric and string values are treated as distinct:

```glx
y = 20
switch (y) {
    case 20 {          // Matches: numeric 20
        print(src="Number")
    }
    case "20" {        // Does NOT match: string "20"
        print(src="String")
    }
}
```

### Pre/Post Increment Operators
GLX supports increment and decrement operators within case blocks:

```glx
value = 45
switch(value) {
    case 45 {
        print(src=--value)  // Pre-decrement: prints 44
    }
}
```

Operators:
- `++value` - Pre-increment (increment then use)
- `value++` - Post-increment (use then increment)
- `--value` - Pre-decrement (decrement then use)
- `value--` - Post-decrement (use then decrement)

## Complete Example

```glx
value = 45
switch(value) {
    case 55 {
        print(src=++value)
    }
    case 45 {
        print(src=--value)
    }
    default {
        print(src="No Such case")
    }
}

y = 20
switch (y) {
    case 20-0 {
        print(src="Working, Best")
    }
    case "20" {
        print(src="Nice, working")
    }
}

you can not write expression in switch's case
```

### Output
```
44
```

## Execution Flow

1. The switch expression is evaluated once
2. Each case value is evaluated and compared with the switch expression
3. When a match is found:
   - The corresponding code block executes
   - Execution continues after the switch statement (no fall-through)
4. If no case matches, the `default` block executes (if present)
5. If no case matches and no `default` exists, execution continues after the switch

## Best Practices

1. **Use meaningful case values**: Make case conditions clear and self-documenting
2. **Include a default case**: Handle unexpected values gracefully
3. **Keep case blocks simple**: Complex logic should be extracted into functions
4. **Order cases logically**: Place most common cases first for readability
5. **Type awareness**: Remember that `20` and `"20"` are different values

## Differences from Other Languages

- **No fall-through**: Unlike C/Java, GLX switch statements don't fall through to the next case
- **No break needed**: Each case automatically exits after execution
- **Expression cases**: Case values can be expressions, not just constants
- **Type-strict matching**: Values must match in both value and type

## Notes

- Switch statements evaluate cases in the order they appear
- Only the first matching case executes
- The switch expression is evaluated only once, improving performance over multiple if-else statements