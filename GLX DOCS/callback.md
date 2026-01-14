# Callback Functions in GLX

GLX supports callback functions as first-class values. Callbacks allow you to pass executable logic into labels, loops, and other control structures, enabling flexible and reusable program design.

This feature makes GLX expressive while keeping control flow simple and predictable.

## What Is a Callback?

A callback in GLX is an anonymous function created using `_call_back_`. It can be:

* Assigned to a variable
* Passed as a parameter
* Invoked dynamically using `_call_`
* Returned from another callback

Callbacks execute in their own scope and can contain any valid GLX statements.

## Callback Syntax

### Defining a Callback
```glx
callback_name = _call_back_ (param1, param2, ...) {
    // callback body
}
```

Example:
```glx
greeting = _call_back_ (name) {
    print(src="Hello Mr. " + name + " How are You")
}
```

### Calling a Callback

Callbacks are invoked using `_call_`:
```glx
_call_ callback_name (arg1, arg2, ...)
```

Arguments are positional and are mapped to parameters in order.

## Example 1: Basic Callback Usage

### Code
```glx
label visit[] main(fn=greet)
{
    _call_ greet ("Danishk Sinha")
}

greeting = _call_back_ (name) {
    print(src="Hello Mr. "+name+" How are You")
}

main(fn=greeting)
```

### Explanation

* `greeting` is a callback that accepts one parameter: `name`
* `main` receives a callback through its parameter `fn`
* `_call_ greet ("Danishk Sinha")` executes the callback
* The callback runs in its own scope

### Output
```
Hello Mr. Danishk Sinha How are You
```

## Example 2: Callback as a Handler (Advanced)

This example demonstrates:

* Passing callbacks into labels
* Executing callbacks inside loops
* Swapping behavior without changing main logic
* Returning values from callbacks

### Main Logic (Callback Consumer)
```glx
label visit[] main(fn=handler)
{
    users = [&l, "Danishk Sinha", "Ali", "Rahul Sharma", "Zoya", "Siddharth", "Noor"]

    print(src="--- Running main() with callback handler ---")

    for u _in_ users {
        _call_ handler (u)
    }

    print(src="--- Done ---")
}
```

### Callback 1: Polite Greeting
```glx
greet_polite = _call_back_ (name) {
    print(src="Hello Mr. " + name + " How are You")
}
```

### Callback 2: Smart Greeting with Logic
```glx
greet_smart = _call_back_ (name) {
    ln = str_len(src=name)

    if ln > 6 {
        print(src="[VIP] Welcome, " + name)
    } else {
        print(src="Hi, " + name)
    }
}
```

### Callback 3: Callback That Returns a Value
```glx
make_tag = _call_back_ (name) {
    tag = "[USER:" + name + "]"
    return tag
}
```

### Using a Returning Callback
```glx
label visit[] demo_return(fn=maker)
{
    n = "Danishk Sinha"
    t = _call_ maker (n)
    print(src="Generated tag => " + t)
}
```

### Running the Examples
```glx
main(fn=greet_polite)
print(src="")

main(fn=greet_smart)
print(src="")

demo_return(fn=make_tag)
```

### Output
```
--- Running main() with callback handler ---
Hello Mr. Danishk Sinha How are You
Hello Mr. Ali How are You
Hello Mr. Rahul Sharma How are You
Hello Mr. Zoya How are You
Hello Mr. Siddharth How are You
Hello Mr. Noor How are You
--- Done ---

--- Running main() with callback handler ---
[VIP] Welcome, Danishk Sinha
Hi, Ali
[VIP] Welcome, Rahul Sharma
Hi, Zoya
[VIP] Welcome, Siddharth
Hi, Noor
--- Done ---

Generated tag => [USER:Danishk Sinha]
```

## Rules & Notes

* Callback arguments are positional
* Argument count must match parameter count
* Callbacks run in a new execution scope
* `return` immediately exits a callback and returns a value
* `break` and `continue` are invalid inside callbacks unless used within loops
* Callbacks are values and can be stored, passed, and reused