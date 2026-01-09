# The import
```
statement in glx is used to bring code (functions, classes, and variables) from one module or package into the current program's, allowing for code reuse, better organization, and access to the vast functionality of the user define method, in glx we do not need to import stander function,

When a module is imported, Glx runs all the code in that module and then makes its public contents available for use in the importing script. Glx ensures that a module is loaded only once per interpreter session, which prevents redundant processing and memory issues. 

```

_1st.glx
```

label visit[] println(src=value) {
    print(src=value)
}

```

_imp.glx
```

import "./_1st.ex"

println(src="Hello, buddy")

// output: Hello, buddy

```