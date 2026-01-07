
# CREATE VARIABLE
```
<variable-name> <equal> <value>

Example:
x = 10
y = 20
sum = x+y

```

# DATA TYPES

```

There are 10 primitive datatype

ByteI(i8),
ByteU(u8),
Int(i128),
UInt(u128),
Float(f64),
BigInt(String),
String(String),
Bool(bool),
Char(char),
Nil,

```

>>> <h2>glx is Dynamic Typed Shell Programming Language</h2>

# _lock_ _unlock_ and _const_

```

name = "danishk"

kprint "Name is "+name
kprint "Making it SmartLock "+name

_lock_ name
_unlock_ name

kprint "Trying to edit"
name = "Bad"
kprint "Edited Successful " 


pi = 2.17

_const_ pi
_unlock_ pi

pi = 55
kprint pi


```

> <h2>_lock_ is temporary constant Storage class</h2>
> <h2>_unlock_ class, unlock a lock variable </h2>
> <h2> If a variable is lock, then you can not assign value</h2>
> <h2>_const_, is a permanent constant storage class</h2>

# kprint
```
kprint is keyword used to print values on screen,
and print(src=) is a print label
```

# NAMED (parameters, args) vs SIMPLE (parameters, args)
```
glx support Named parameters and Named args

simple label call
    
    foo(value)
    bar(value)

named parameter label call

    print(src=value)
    foo(tar=value)
    bar(x=some)

```


# trash variables

_kill_ deletes any variable and sends it to the trash. By default, whenever you retrieve a value normally,
the memory is freed. If a variable has been killed, it goes into trash storage, and only the _revive_ keyword can recover it from the trash. Remember, only variables that are in the trash can be revived.

```


x = "danishk sinha"
PI = 3.14

_kill_ x
_revive_ x

print(src=x)

_kill_ PI
_revive_ PI

print(src=PI)

```

# pass keyword
The pass keyword in glx is a null operation (NOP) statement used as a placeholder where a statement is syntactically required but no action is needed or desired yet. The Python interpreter executes pass, but it does nothing, allowing the program to continue without syntax errors. 
Purpose and Use Cases
The primary use of pass is to create syntactically valid empty code blocks during the development process.
Glx uses curly braces to define code blocks, and an empty block will cause a SyntaxError. The pass statement fills this gap. 

```


label visit[] main()
{
    if(true) {
        pass
    } else {
        pass
    }

    pass
}
```