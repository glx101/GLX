
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

