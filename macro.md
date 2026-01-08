
# Macro

## _define_

```
`_define_` is used to define a macro. 
If you define a macro and then call it, the entire macro body will be expanded at the point of the call,
and the macro arguments will be assigned to new variables.
```

```

// ==========================================================
// Verify, Macro expansion!

// macro definition
_define_ addition(x, y) [
    print(src=x + y)
]


label visit[] test() {

    // macro call
    #addition(4, 5)
}


test()
// 9

// ===========================================================
// Verify, is macro expansion is really happening ?

_define_ subtract() [
    print(src=x-y)
]

label visit[] main() {
    x = 10
    y = 4
    #subtract()
}

main()
// output 9
// This is show proof, macro expansion is happening!
```


The `_define_` keyword is used to define a macro.
Whenever a macro is called, it expands at the point of the macro call, and the macro arguments are bound to a variable.

```
_define_ subtract(name) [
    print(src=x-y)
]

label visit[] main() {
    x = 10
    y = 4
    #subtract("danishk")

    // proof
    print(src=name)
}

main()


PATH=[/home/danishk/Documents/GLX] USER=[danishk]% ./Test.glx
6
danishk
PATH=[/home/danishk/Documents/GLX] USER=[danishk]% 

```

# _ifndef , _endif_, _undef_

```
`ifndef` is a runtime condition, meaning that if a macro is not defined, the macro inside it should be defined. If it has already been defined, do not define it again. It acts like a gatekeeper that only runs if the macro inside it is not already defined. If it has been defined before, it is skipped directly; otherwise, the definition starts from the beginning. `endif` is a terminating guard that ends the `ifndef` block. Remember that it's best to define only one macro within an `ifndef` block. Defining multiple macros is incorrect.
```

```

_ifndef_ DEBUG
    
    _define_ DEBUG(x) [
        kprint name
        kprint "DEBUG IS ON"
        kprint msg
        kprint x
    ]

_endif_

_define_ ADDITION() [
    kprint x+y
]

label visit[] greeting() {
    
    name = "Danishk"
    msg = "Hello, budddy"

    #DEBUG(msg)
}

greeting()

x = 10
y = 20
#ADDITION()

_undef_ DEBUG
_undef_ ADDITION
```

```
`#undef` instructs the preprocessor to undefine any previously defined macro.  If you try to access that macro after it has been undefined, it will likely result in an error.
```