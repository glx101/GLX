
# Switch–Case in GLX


In GLX, the switch–case statement is a structured control-flow construct used to execute one block of code from multiple possibilities based on the value of a single evaluated expression. It is designed to be clean, readable, and deterministic, making it a better alternative to long chains of if–elif–else statements when checking one variable against multiple fixed values.
In the given example:

age = 2 + 3



the expression is evaluated first, producing the value 5. This value is then passed to the switch statement for comparison.
Key Components in GLX Switch–Case

switch expression
The expression inside switch ( ... ) is evaluated once. Its resulting value is used for comparison with each case. In GLX, this expression can be a computed value, not just a variable.

case blocks
Each case defines a constant match value followed by a code block enclosed in braces { }. When the switch value matches a case value exactly, only that case’s block is executed.

implicit break behavior
Unlike C-like languages, GLX does not require an explicit break statement. Once a matching case is executed, control automatically exits the switch block. This eliminates accidental fall-through bugs and keeps logic predictable.

default block
The default block is optional and is executed only when no case value matches the switch expression. It acts as a safe fallback, similar to else in conditional statements.

Execution Flow in GLX

The expression inside switch is evaluated.
The resulting value is compared against each case value.
When a match is found, the corresponding case block is executed.
The switch statement terminates immediately after executing the matched case.
If no case matches and a default block exists, the default block is executed.

Example Result Explained
age = 2 + 3


The value of age becomes 5
case 5 matches
Output produced:
age is 5


This confirms that GLX switch–case behavior is expression-driven, safe, and non-fallthrough by design, making it ideal for clear and maintainable control flow.


```


age = 2+ 3

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


os = "linux"

switch (os) 
{
    case "win" {
        print(src="Windows OS")
    }
    case "linux" {
        print(src="Linux Os")
    }
    case "darvin" {
        print(src="Macros")
    }
}
}


PATH=[/home/danishk/Documents/GLX] USER=[danishk]% ./Test.glx
age is 5
Linux Os
PATH=[/home/danishk/Documents/GLX] USER=[danishk]%
```